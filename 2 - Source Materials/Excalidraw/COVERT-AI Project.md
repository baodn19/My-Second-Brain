---
excalidraw-plugin: parsed
tags:
  - excalidraw
  - "#Project"
categories:
  - "[[Projects]]"
year: 2026
status:
  - completed
---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'

# Summary (250 words)
COVERT-AI is a chat assistant that can live transcribe audio, ingest video, retrieve context from documents, and speak answers in real-time. Compared to the desktop app prototype, COVERT-AI implemented Dockerized micro-services and React frontend, improving capability and scalability. 

COVERT-AI has 



# Trials & Errors
| Problems                                                                                                             | Solution                                                                                                                                                                              | Take-away                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| The instance I install NVIDIA driver on a Linux machine and restart, the kernel changed and removed the wifi driver. | Download the kernel (.deb) on another machine with the same distribution and version $\to$ Transfer the kernel file through USB $\to$ Install the kernel file and restart the machine | Always backup the kernel before installing or updating NVIDIA driver                                           |
| I ran RAGBench on the PubmedQA and the entire last trial encounter an error of exceeding API usage.                  | Ask to raise the cap                                                                                                                                                                  | Be cautious when benchmarking on big dataset. Make sure to ask supervisor before running.                      |
| I forget to delete the API keys when running LLM in Cursor and VSC                                                   | Fill in the API Key when composing the Docker container and removing after composing container                                                                                        | This only works for repository with composing Docker container                                                 |
| Resolving a merge conflict deletes the feature on the working branch                                                 | Ditch than branch and restart the feature from the commit that the feature is still working                                                                                           | -Only do single feature branch<br>-Don't split a branch into smaller single feature branch. Work with you have |
|                                                                                                                      |                                                                                                                                                                                       |                                                                                                                |
## Convention
| Convention                                                                                                                                                                                                                                   | Purpose                                                                                                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
# Concepts
## Knowing who talked talked when and what
- *Combine ASR and diarization:*
	- Diarization: Produce RTTM (Rich Transcription Time Marked) to tell **who spoke at specific time** (annonymously)
	- ASR (Automatic Speech Recognition): **Differentiate** the speaker and **what they said**


# Related Experience
- [[RAGBench Experience]]
- [[RAG Experience]]
- [[CPU vs GPU Video Ingestion]]
# Error log
- [ ] Transcription is duplicated in history tab
![[COVERT-AI - Transcription Duplicate Error.png]]
- [ ] d
# Excalidraw Data

## Text Elements
Observation Metrics ^Jj1Fgf92

1. Speaker label accuracy: 
- Overlap: during and after overlap, does each stretch of audio get the right speaker ID?
- Short turns: can it follow rapid turn-taking, not only long monologues?
2. Speaker count (false splits / merges)
- 2 speakers: Baseline turn-taking; false splits (one person → 2 IDs)
- 3-4 speakers: meeting-like
3. Boundary delay: How long does the system take to reflect the change in speaking state in real-time? ^NoS2tkXq

Testing ^mpNokXYv

Frontend ^jAKSID3U

Backend ^NfFdXh7g

Client Layer ^vG8N8KH3

UI ^BAaVzkfQ

Diarization: diar_streaming_sortformer_4spk-v2.1
Multitalker ASR: multitalker-parakeet-streaming-0.6b-v1 ^lPiTJyDK

%%
## Drawing
```compressed-json
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
```
%%