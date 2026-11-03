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

Questions ^ntydjAen

- Given  ^TkkT4hT9

%%
## Drawing
```compressed-json
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
```
%%