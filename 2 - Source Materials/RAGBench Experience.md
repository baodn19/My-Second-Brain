---
categories:
  - "[[Experience]]"
modified: May 23rd 2026, 1:08:40 pm
---
# Theory

# Experience
## [[ablation study]] of [[RAG]] pipeline
- *Overview:* run 3 trials with the same LLM model and compare the [[ROUGE]] values of each trials
- *Trials:*

|**Trial**|**Active Components**|**Ablated (Removed) Component**|**Metric Evaluated**|
|---|---|---|---|
|**1: All Documents**|Retrieval + Augmentation + Generation|None (Full System)|End-to-end pipeline effectiveness.|
|**2: Relevant Documents**|Augmentation + Generation|Active Retrieval Search|LLM synthesis capabilities and impact of distractor noise (Oracle condition).|
|**3: No Documents**|Generation|Retrieval + Augmentation|Baseline parametric knowledge of the LLM.|
- *Desired outcomes:* 
	- Trial 1 has the greatest ROUGE values mean the retriever effectively return relevant information.
	- Trial 2 has the second greatest ROUGE values. This demonstrates that chunking texts and vectorizing them to rank relevancy is superior
	- Trial 3 has the lowest ROUGE values. This indicates the RAG pipeline improves the answer.
### Metrics to include
- *Retrieval evaluation:*
	- Hit rate:
		- Hit@1: the percentage that the first retrieved chunk belongs to the ground truth document
		- Hit@K: the percentage that for every question, at least a chunk belongs to the ground truth document
	- Precision@K: the percentage of retrieved chunks that belong to the ground truth document (mean and median)
- *Generation evaluation:*
	- ROUGE values: evaluate generated response based on lexical overlap (less effective)
	- BERTScore: evaluate generated response based on semantic similarity using contextual embeddings (more effective)
### Choosing subset for evaluation
- *Retrieval:* long document length so each documents gets chunked into many pieces $\implies$ Notice Hit@K and Precision@K
- *MS Macro:* subset with the most documents, testing if the retriever can find the relevant chunks  
- *HotpotQA:* test on multi-hop to evaluate synthesizing information from many documents

# Questions

