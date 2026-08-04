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

%%
## Drawing
```compressed-json
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
```
%%