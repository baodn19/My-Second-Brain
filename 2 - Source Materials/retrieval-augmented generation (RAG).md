---
created: March 12th 2026
categories:
  - "[[Concepts]]"
modified: March 12th 2026, 4:25:17 pm
tags:
  - llm
source: https://www.youtube.com/watch?v=T-D1OfcDW1M
---
- *Problem:*
	1. No source
	2. Out of date data
- *Retrieval:* looks at data store to get the most up-to-date information $\implies$ Solves **problem 1**
	- Rely less on trained data $\implies$ Reduce hallucination
	- **Pros:** can say "I don't know" if the [[LLM]]s can't reliably answer the question with the data store
	- **Cons:** if the retriever is not good enough, the question won't get answered despite being answerable
- *Augment:* add latest data to the data store $\implies$ Solves **problem 2**
- *Prompt:* has 3 parts
	1. Instructions to pay attention to retrieved content
	2. User's question
	3. **Generate** response with source citation
