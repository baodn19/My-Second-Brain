---
created: 2026-05-19
modified: June 7th 2026, 10:46:38 pm
categories:
  - "[[Projects]]"
type: []
org: []
start:
year:
url:
status:
---

| Problems                                                                                                             | Solution                                                                                                                                                                              | Take-away                                                                                 |
| -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| The instance I install NVIDIA driver on a Linux machine and restart, the kernel changed and removed the wifi driver. | Download the kernel (.deb) on another machine with the same distribution and version $\to$ Transfer the kernel file through USB $\to$ Install the kernel file and restart the machine | Always backup the kernel before installing or updating NVIDIA driver                      |
| I ran RAGBench on the PubmedQA and the entire last trial encounter an error of exceeding API usage.                  | Ask to raise the cap                                                                                                                                                                  | Be cautious when benchmarking on big dataset. Make sure to ask supervisor before running. |
| I forget to delete the API keys when running LLM in Cursor and VSC                                                   | Fill in the API Key when composing the Docker container and removing after composing container                                                                                        | This only works for repository with composing Docker container                            |
# Related experience
- [[RAGBench Experience]]
- [[RAG Experience]]