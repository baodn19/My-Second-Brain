---
modified: June 23rd 2026, 12:55:59 pm
---
## 1. Fidelity: what each path can process and retrieve

### Path 1 — Lightweight CPU (`file_service`)

**Ingestion fidelity**

| Modality | Coverage | Limitations |
|----------|----------|-------------|
| **Audio** | Full-track transcript (AssemblyAI or faster-whisper) | No speaker diarization; no segment-level alignment with visuals |
| **Visual** | One frame every **5 s** (configurable); MSE dedup skips static scenes | Each frame is captioned **in isolation** (2–4 sentences). No motion, no multi-frame context, no cross-frame reasoning |
| **Temporal** | Timestamps on frame captions only | Anything between sampled frames is invisible unless spoken in audio |
| **Semantic structure** | None — flat text block | No entities, relations, or cross-video links |

**Retrieval fidelity**

- Query path: unified Assistant → `meeting_service` → `POST file_service/search/`
- Mechanism: **embedding similarity only** (FAISS, default **top-5**, ~1000-char chunks)
- Retrieves **text chunks** — whatever made it into `[TRANSCRIPT]` / `[FRAMES]`
- Cannot retrieve raw pixels, motion, or visual features the caption missed
- Same retrieval quality as PDFs/images: good for “what was said” or “what was clearly visible on a sampled frame,” weak for fine visual detail, action between frames, or cross-segment reasoning

**Best for:** spoken content, slides/on-screen text, obvious scene changes. 
**Weak for:** subtle visuals, fast action, long silent sections, complex multi-hop video reasoning.

---

### Path 2 — Deep GPU VideoRAG (`videorag_service`)

**Ingestion fidelity**

| Modality | Coverage | Limitations |
|----------|----------|-------------|
| **Audio** | Whisper ASR **per 30 s segment** | Cloud API; segment-boundary artifacts possible |
| **Visual (indexing)** | **5 frames/segment** during indexing; captions use **transcript + frames together** (gpt-4o) | Still text-derived at index time, but richer than Path 1 |
| **Visual (query)** | **ImageBind** 1024-d embeddings per segment; **15 frames** re-captioned on retrieved segments at query time | Visual retrieval stays inside `videorag_service` |
| **Semantic structure** | **Knowledge graph** (entities + relations) across segments/videos | LLM-extracted; quality depends on model and content |
| **Cross-video** | Entity unification and graph traversal | Designed for long / multi-video corpora |

**Retrieval fidelity — two modes**

| Mode | Mechanism | Fidelity |
|------|-----------|----------|
| **Video Chat** (`POST /sessions/{chat_id}/query`) | Hybrid: text-chunk search + **KG entity traversal** + **ImageBind visual matching** + LLM segment filter + keyword-aware re-caption | **Highest** — vision-aware, segment-level, graph-aware |
| **Unified Assistant** (via FAISS back-fill) | Text only: segment transcript+captions + entity/relation strings pushed through `faiss_bridge` | **Same class as Path 1** for Assistant search — no ImageBind in FAISS |

So Path 2 is strictly better for dedicated video Q&A, but the **shared Assistant only sees the text slice** of Path 2’s index, not the visual vectors.

---

## 2. Form of processed video

| Aspect                  | Path 1                                                   | Path 2                                                                                                  |
| ----------------------- | -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Primary artifact**    | Single structured **text block**                         | Multi-store **VideoRAG index** per `(user, chat)` session                                               |
| **Text format**         | `[TRANSCRIPT]` + `[FRAMES]` with `t=X.Xs:` timestamps    | Per-segment content in `kv_store_video_segments.json`                                                   |
| **Knowledge graph**     | None                                                     | NetworkX graph (`graph_chunk_entity_relation.graphml`)                                                  |
| **Vector indexes**      | FAISS text embeddings only (shared `file_service` index) | **Three** local stores: text chunks, entity embeddings, **ImageBind segment features** (NanoVectorDB)   |
| **Shared FAISS output** | Direct: `_index_text()` → ~1000-char chunks              | Indirect: `faiss_bridge.push_to_faiss()` → pre-chunked segment text + `[Entity]` / `[Relation]` strings |
| **Stable key**          | Upload filename key                                      | `video:{user_id}:{chat_id}:{video_name}`                                                                |
|                         |                                                          |                                                                                                         |
- videos.py (Path 1):
``` python
def video_to_text(video_path: str) -> str:
    ...
        [TRANSCRIPT]
        <full audio transcript>

        [FRAMES]
        t=5.0s: <vision caption>
        t=10.0s: <vision caption>
```
- faiss_bridge.py (Path 2):
```python
def _segment_chunks(working_dir: str, video_name: str) -> list[str]:
    """Per-segment transcript+caption text from kv_store_video_segments.json."""
    ...
def _graph_chunks(working_dir: str) -> list[str]:
    """Entity and relation descriptions from the knowledge graph."""
```

**Design boundary:** ImageBind vectors **never** enter FAISS — different embedding space. Visual retrieval is Video Chat only.

---

## 3. Resource requirements

### Path 1 — Lightweight CPU

| Resource | Requirement |
|----------|-------------|
| **GPU** | **Not required** — runs inside `file_service` |
| **Compute** | FFmpeg (local) + OpenCV frame scan (CPU) |
| **External APIs** | STT (AssemblyAI cloud, or local faster-whisper) + **one vision API call per kept frame** |
| **Latency model** | **Synchronous** — upload blocks until processing finishes |
| **Scaling cost drivers** | Video length ÷ frame interval (minus dedup) → vision API calls; e.g. 1 h @ 5 s ≈ **720 captions** worst case |
| **Storage** | FAISS chunks only; no session working dirs |
| **Container** | No extra service — piggybacks on `file_service` |

Tunable via env:

```env
VIDEO_FRAME_INTERVAL_SECS=5   # higher = fewer vision calls, lower visual fidelity
VIDEO_MSE_THRESH=500          # higher = more dedup, fewer calls on static video
```

---

### Path 2 — Deep GPU VideoRAG

| Resource | Requirement |
|----------|-------------|
| **GPU** | **Required** — ImageBind on NVIDIA GPU (`docker-compose.gpu.yml`) |
| **Model disk** | ImageBind checkpoint **~4.5 GB** (`imagebind_huge.pth`) |
| **Container** | Dedicated `videorag_service`: PyTorch 2.8 + CUDA 12.8, ffmpeg, ImageBind, MoviePy, NetworkX |
| **Concurrency** | `VIDEORAG_WORKERS=2` default; ImageBind is **lock-serialized** — more workers mostly queue |
| **External APIs** | OpenAI for Whisper ASR, gpt-4o captions, entity extraction, embeddings, and query-time LLM filtering/re-caption |
| **Latency model** | **Async** — upload returns immediately; poll `/status` until indexing completes |
| **Scaling cost drivers** | Per video: split into 30 s segments × (ASR + caption + ImageBind encode + graph extraction); query adds visual retrieval + up to 15-frame re-caption on matched segments |
| **Storage** | Persistent session dirs under `VIDEORAG_STORAGE`: segments, graph, vector DBs, uploads |
| **Operational caveats** | FAISS back-fill can fail if JWT expires on long jobs; `file_service` restart drops FAISS but VideoRAG index persists |

Indexing defaults from the engine:
- videorag.py:
``` python
    video_segment_length: int = 30 # seconds
    rough_num_frames_per_segment: int = 5 # frames
    fine_num_frames_per_segment: int = 15 # frames
    ...
    retrieval_topk_chunks: int = 2
```

---

## Side-by-side summary

| Question | Path 1 (CPU) | Path 2 (GPU VideoRAG) |
|----------|--------------|------------------------|
| **Data fidelity** | Full audio + sparse static frames | Segment-aligned audio+vision + ImageBind + knowledge graph |
| **Retrieval fidelity (Assistant)** | Text embedding search (top-5) | Text back-fill only — similar Assistant experience, richer source text |
| **Retrieval fidelity (Video Chat)** | N/A | Hybrid text + graph + visual — highest |
| **Processed form** | Flat text → FAISS | Graph + multi-vector index locally; text subset → FAISS |
| **GPU** | None | Required |
| **API cost** | ~1 vision call / ~5 s of video | Many calls per 30 s segment + query-time re-caption |
| **Time to usable** | Blocks upload until done | Async; minutes for long videos |
| **Best tradeoff** | Quick ingest, no GPU, “good enough” text search | Deep video understanding, long/multi-video, vision-aware Q&A |

**Practical rule:** Use Path 1 when you want video in the same bucket as documents with minimal infra. Use Path 2 when visual semantics, segment-level retrieval, or cross-video entity reasoning matter — and use **Video Chat** for the full benefit; the FAISS back-fill is mainly so the unified Assistant can **cite** video text, not **see** it the way VideoRAG does.