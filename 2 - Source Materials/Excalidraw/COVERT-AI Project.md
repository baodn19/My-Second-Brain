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
| Convention                                                                                                                                                | Purpose                                                                                |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Git history should only have 2 lines, blue for current branch and yellow for main. Make sure to pull code from main everyday to keep your code up-to-date | Avoid code diverging and people's code conflicting each other                          |
| Delete remote & local branch after merging                                                                                                                | Keep the repository clean and to highlight working branches                            |
| Have a switch to turn off any broken features                                                                                                             | Avoid that features breaking the whole application and isolate broken feature to debug |
| Paths (NEMO_PATH, PYTHONPATH) declaration and removal for a conda project should be integrated into the venv activation and deactivation.                 | Avoid PYTHONPATH having unnecessary paths and keeping the path to the project itself   |
| Use `python-dotenv` to read `.env` files. Don't use placeholders value for `.env.example`, instead use comments                                           | Avoid writing functions to parse keys from `.env`.                                     |
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

Diarization: diar_streaming_sortformer_4spk-v2.1
Multitalker ASR: multitalker-parakeet-streaming-0.6b-v1 ^lPiTJyDK

%%
## Drawing
```compressed-json
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
```
%%