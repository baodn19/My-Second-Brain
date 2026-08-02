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

%%
## Drawing
```compressed-json
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=
```
%%