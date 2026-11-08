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

Questions ^ntydjAen

- Given context throughout speech, can the model associate the index speaker with someone in a directory? ^TkkT4hT9

Audio Collecting Procedure ^EfE0FAIK

Put one phone in the center of the table. Its recording is what you feed to Covert AI.
Have each speaker also record on their own phone held close to them.
Clap once at the start so you can line up all five recordings.
Run voice activity detection on each close recording (Silero VAD works well). Because each phone mostly hears one person, this gives you each speaker’s talk times, overlaps included. Spot-check the results in Audacity. ^paihTUQk

%%
## Drawing
```compressed-json
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=
```
%%