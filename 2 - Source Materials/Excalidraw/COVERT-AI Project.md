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
-  ^NoS2tkXq

%%
## Drawing
```compressed-json
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=
```
%%