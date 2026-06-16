---
categories:
  - "[[Experience]]"
modified: June 16th 2026, 3:26:20 pm
---
# Theory
- [[frielRAGBenchExplainableBenchmark2025]]

# Experience
## [[ablation study]] of [[RAG]] pipeline
- *Overview:* run 3 trials with the same LLM model and compare the [[ROUGE]] values of each trials
- *Trials:*

| **Trial**                 | **Active Components**                                         | **Ablated (Removed) Component** | **Metric Evaluated**                                                          |
| ------------------------- | ------------------------------------------------------------- | ------------------------------- | ----------------------------------------------------------------------------- |
| **1: All Documents**      | Retrieval (Corpus) + Augmentation + Generation                | None (Full System)              | End-to-end pipeline effectiveness.                                            |
| **2: Relevant Chunk**     | Augmentation + Generation                                     | Retrieval                       | LLM synthesis capabilities given the correct context                          |
| **3: Relevant Documents** | Retrieval (Ground Truth Document) + Augmentation + Generation | None (Reduce retrieving scope)  | LLM synthesis capabilities and impact of distractor noise (Oracle condition). |
| **4: No Documents**       | Generation                                                    | Retrieval + Augmentation        | Baseline parametric knowledge of the LLM.                                     |
- *Desired outcomes:* ranking in highest generation metrics (see below)
	- Questions supported by document: T2 > T3 $\approx$ T1 > T4
	- Questions **not** supported by document: T4 > T2 > T3 > T1
### Metrics to include
- *Retrieval evaluation:*
	- Hit rate:
		- Hit@1: the percentage that the first retrieved chunk belongs to the ground truth document
		- Hit@K: the percentage that for every question, at least a chunk belongs to the ground truth document
	- Precision@K: the percentage of retrieved chunks that belong to the ground truth document (mean and median)
	- Recall@K: the percentage of ground truth document covered by the top-K chunks
- *Generation evaluation:*
	- ROUGE values: evaluate generated response based on lexical overlap (less effective)
	- BERTScore: evaluate generated response based on semantic similarity using contextual embeddings (more effective)
### Choosing subset for evaluation
- *Retrieval:* long document length so each documents gets chunked into many pieces $\implies$ Notice Hit@K and Precision@K
- *MS Macro:* subset with the most documents, testing if the retriever can find the relevant chunks  
- *HotpotQA:* test on multi-hop to evaluate synthesizing information from many documents

## Untracked files that you wished to keep should be copied outside of the repo folder

# Questions

