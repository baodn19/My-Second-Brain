---
title: "[[RAGBench - Explainable Benchmark for Retrieval-Augmented Generation Systems]]"
year: 2025 
authors: Robert Friel, Masha Belyi, Atindriyo Sanyal
categories:
  - "[[Research References]]"
tags: 
- Computer-Science---Artificial-Intelligence 
- Computer-Science---Computation-and-Language 
---

Zotero PDF Link: [[Zotero Attachments/Friel et al. - 2025 - RAGBench Explainable Benchmark for Retrieval-Augmented Generation Systems.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"Abstract"</mark> [Page 1](zotero://open-pdf/library/items/CU58LZDS?page=1&annotation=6ZSZJTDF) 
  
 <mark class="hltr-yellow">"TRACe evaluation framework: a set of explainable and actionable RAG evaluation metrics applicable across all RAG domains."</mark> [Page 1](zotero://open-pdf/library/items/CU58LZDS?page=1&annotation=XLLJKKGU) 
  
 <mark class="hltr-purple">"1 Introduction"</mark> [Page 1](zotero://open-pdf/library/items/CU58LZDS?page=1&annotation=WI5LT47X) 
  
 <mark class="hltr-purple">"2 Related Work"</mark> [Page 2](zotero://open-pdf/library/items/CU58LZDS?page=2&annotation=Q9CU2BXE) 
  
 <mark class="hltr-purple">"3 RAGBench Construction"</mark> [Page 3](zotero://open-pdf/library/items/CU58LZDS?page=3&annotation=NNZ5ZG2Y) 
  
 <mark class="hltr-purple">"3.1 Component Datasets"</mark> [Page 3](zotero://open-pdf/library/items/CU58LZDS?page=3&annotation=YKLYUQB6) 
  
 <mark class="hltr-yellow">"five distinct domains"</mark> [Page 3](zotero://open-pdf/library/items/CU58LZDS?page=3&annotation=HT7EDHWW) 
  
 <mark class="hltr-yellow">"bio-medical research"</mark> [Page 3](zotero://open-pdf/library/items/CU58LZDS?page=3&annotation=H2ARFAVP) 
  
 <mark class="hltr-yellow">"general knowledge"</mark> [Page 3](zotero://open-pdf/library/items/CU58LZDS?page=3&annotation=V9MBBP9Z) 
  
 <mark class="hltr-yellow">"legal contracts"</mark> [Page 3](zotero://open-pdf/library/items/CU58LZDS?page=3&annotation=ETBHNN7S) 
  
 <mark class="hltr-yellow">"customer support"</mark> [Page 3](zotero://open-pdf/library/items/CU58LZDS?page=3&annotation=GVBVNLAA) 
  
 <mark class="hltr-yellow">"finance"</mark> [Page 3](zotero://open-pdf/library/items/CU58LZDS?page=3&annotation=7VV5LP6U) 
  
 <mark class="hltr-yellow">"For each component dataset we generate responses with LLMs"</mark> [Page 4](zotero://open-pdf/library/items/CU58LZDS?page=4&annotation=BP4ANR9H) 
  
 <mark class="hltr-yellow">"We set the temperature to 1.0 for generation."</mark> [Page 4](zotero://open-pdf/library/items/CU58LZDS?page=4&annotation=MYTFVEHA) 
  
 <mark class="hltr-purple">"3.2 TRACe Evaluation Framework"</mark> [Page 4](zotero://open-pdf/library/items/CU58LZDS?page=4&annotation=A2ADZ7TX) 
  
 <mark class="hltr-yellow">"The retriever should precisely return all the necessary information to address the user"</mark> [Page 4](zotero://open-pdf/library/items/CU58LZDS?page=4&annotation=5WUUI3SE) 
  
 <mark class="hltr-yellow">"query, avoiding any superfluous data."</mark> [Page 5](zotero://open-pdf/library/items/CU58LZDS?page=5&annotation=7R98AMEI) 
  
 <mark class="hltr-yellow">"The generator must effectively utilize the retrieved information, ensuring the response is strictly based on the provided context without introducing any hallucinations in the output."</mark> [Page 5](zotero://open-pdf/library/items/CU58LZDS?page=5&annotation=ZPPE66LF) 
  
 <mark class="hltr-yellow">"Utilization, Adherence, and Completeness measure the quality of the generator."</mark> [Page 5](zotero://open-pdf/library/items/CU58LZDS?page=5&annotation=WNQZMWZ9) 
  
 <mark class="hltr-yellow">"Adherence"</mark> [Page 5](zotero://open-pdf/library/items/CU58LZDS?page=5&annotation=2UIQJQVV) 
  
 <mark class="hltr-yellow">"how well an LLM output adheres to a source of factual information"</mark> [Page 5](zotero://open-pdf/library/items/CU58LZDS?page=5&annotation=9293GJ4Y) 
  
 <mark class="hltr-yellow">"Relevance measures the quality of the retriever output with respect to the query."</mark> [Page 5](zotero://open-pdf/library/items/CU58LZDS?page=5&annotation=TLQ7VM3R) 
  
 <mark class="hltr-yellow">"D be a set of context documents {d1...dn} retrieved for a RAG input query."</mark> [Page 5](zotero://open-pdf/library/items/CU58LZDS?page=5&annotation=UN89ZIJT) 
  
 <mark class="hltr-yellow">"a set of relevant tokens in di as Ri = {t1, ...tr}"</mark> [Page 5](zotero://open-pdf/library/items/CU58LZDS?page=5&annotation=FMEDEAPT) 
  
 <mark class="hltr-yellow">"Ui = {t1, ...tu} as the set of utilized tokens in document di, which reflect information that the generation model is using to produce a response."</mark> [Page 5](zotero://open-pdf/library/items/CU58LZDS?page=5&annotation=H7XNLDT6) 
  
 <mark class="hltr-purple">"3.3 RAGBench Statistics"</mark> [Page 6](zotero://open-pdf/library/items/CU58LZDS?page=6&annotation=TZD6JCNH) 
  
 <mark class="hltr-purple">"3.4 LLM annotator"</mark> [Page 6](zotero://open-pdf/library/items/CU58LZDS?page=6&annotation=PMGMUIBI) 
  
 <mark class="hltr-purple">"3.5 RAG Case Study"</mark> [Page 8](zotero://open-pdf/library/items/CU58LZDS?page=8&annotation=V6NLYTL9) 
  
 <mark class="hltr-purple">"4 Experiments"</mark> [Page 8](zotero://open-pdf/library/items/CU58LZDS?page=8&annotation=VKFGFZG4) 
  
 <mark class="hltr-purple">"4.1 LLM Judge"</mark> [Page 8](zotero://open-pdf/library/items/CU58LZDS?page=8&annotation=JRUXER3Z) 
  
 <mark class="hltr-purple">"4.2 Fine-tuned Judge"</mark> [Page 8](zotero://open-pdf/library/items/CU58LZDS?page=8&annotation=ESRNSGED) 
  
 <mark class="hltr-purple">"4.3 Evaluation"</mark> [Page 8](zotero://open-pdf/library/items/CU58LZDS?page=8&annotation=HHEWLEKI) 
  
 <mark class="hltr-purple">"5 Results"</mark> [Page 9](zotero://open-pdf/library/items/CU58LZDS?page=9&annotation=823CCRMF) 
  
 <mark class="hltr-purple">"6 Conclusion"</mark> [Page 9](zotero://open-pdf/library/items/CU58LZDS?page=9&annotation=75GZQGPH) 
  
 <mark class="hltr-purple">"7 Appendix"</mark> [Page 14](zotero://open-pdf/library/items/CU58LZDS?page=14&annotation=SAP7T8JM) 
  
 <mark class="hltr-purple">"7.1 RAGBench Code and Data"</mark> [Page 14](zotero://open-pdf/library/items/CU58LZDS?page=14&annotation=2J8PHUXC) 
  
 <mark class="hltr-purple">"7.2 RAGBench Dataset Details"</mark> [Page 14](zotero://open-pdf/library/items/CU58LZDS?page=14&annotation=KPZZHAPI) 
  
 <mark class="hltr-purple">"7.3 Response Generation Prompt"</mark> [Page 16](zotero://open-pdf/library/items/CU58LZDS?page=16&annotation=ZMXGUIXU) 
  
 <mark class="hltr-purple">"7.4 GPT Labeling Prompt"</mark> [Page 16](zotero://open-pdf/library/items/CU58LZDS?page=16&annotation=2EV8BFHI) 
  
 <mark class="hltr-purple">"7.5 Annotation Post-Processing Steps"</mark> [Page 18](zotero://open-pdf/library/items/CU58LZDS?page=18&annotation=RKLYJXPK) 
  
 <mark class="hltr-purple">"7.6 Annotation Alignment with Human Judgements"</mark> [Page 18](zotero://open-pdf/library/items/CU58LZDS?page=18&annotation=FG5W4ACG) 
  
 <mark class="hltr-purple">"7.6.1 Adherence Alignment with DelucionQA"</mark> [Page 18](zotero://open-pdf/library/items/CU58LZDS?page=18&annotation=LWKNUNFI) 
  
 <mark class="hltr-purple">"7.6.2 Relevance and Utilization Alignment with DelucionQA"</mark> [Page 19](zotero://open-pdf/library/items/CU58LZDS?page=19&annotation=6GSCLLCG) 
  
 <mark class="hltr-purple">"7.6.3 Rank-based Alignment for Adherence and Relevance"</mark> [Page 19](zotero://open-pdf/library/items/CU58LZDS?page=19&annotation=S23CNAHR) 
  
 <mark class="hltr-purple">"7.7 RAG Case Study"</mark> [Page 19](zotero://open-pdf/library/items/CU58LZDS?page=19&annotation=SEMYYYCZ) 
  
 <mark class="hltr-purple">"7.8 DeBERTa model training"</mark> [Page 20](zotero://open-pdf/library/items/CU58LZDS?page=20&annotation=JL5XBM4I) 
  
