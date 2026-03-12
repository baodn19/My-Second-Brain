---
title: "[[Retrieval-Augmented Robots via Retrieve-Reason-Act]]"
year: 2026 
authors: Izat Temiraliev, Diji Yang, Yi Zhang
categories:
  - "[[Research References]]"
tags: 
- Computer-Science---Artificial-Intelligence 
- Computer-Science---Robotics 
---

Zotero PDF Link: [[Zotero Attachments/Temiraliev et al. - 2026 - Retrieval-Augmented Robots via Retrieve-Reason-Act.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"ABSTRACT"</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=RNGUL272) 
  
 <mark class="hltr-yellow">"To achieve general-purpose utility, we argue that robots must evolve from passive executors into active Information Retrieval users."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=RA3HFS8G) 
  
 <mark class="hltr-orange">"In strictly zero-shot settings where no prior demonstrations exist, robots face a critical information gap, such as the exact sequence required to assemble a complex furniture kit, that cannot be satisfied by internal parametric knowledge (common sense) or past internal memory."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=ML4VLS63) 
  
 <mark class="hltr-yellow">"While recent robotic works attempt to use search before action, they primarily focus on retrieving past kinematic trajectories (analogous to searching internal memory) or text-based safety rules (searching for constraints)."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=V9UXKL5T) 
  
 <mark class="hltr-orange">"These approaches fail to address the core information need of active task construction: acquiring unseen procedural knowledge from external, unstructured documentation."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=FUSQGJ4G) 
  
 <mark class="hltr-yellow">"bridges the gap between visual documentation and physical actuation."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=G7ZRJT48) 
  
 <mark class="hltr-purple">"1 INTRODUCTION"</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=NLDHSUFD) 
  
 <mark class="hltr-orange">"While Large Language Models (LLMs) [1, 11] and Vision-Language Models (VLMs) [10] have demonstrated impressive capabilities in semantic reasoning [2, 20], they face a fundamental limitation when interacting with complex physical objects: the gap between semantic understanding and procedural execution [3]."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=NXZ9ZKJZ) 
  
 <mark class="hltr-orange">"Furthermore, in long-horizon tasks, relying on internal parametric memory to store an exhaustive library of assembly sequences is both inefficient and unscalable."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=YCRDIWBQ) 
  
 <mark class="hltr-yellow">"this approach as Retrieval-Augmented Robotics (RAR), where agents actively query external memory to retrieve the procedural context required to ground their physical actions."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=QRWHDKX5) 
  
 <mark class="hltr-yellow">"Approaches like STRAP [6] and RAEA [25] focus on experience retrieval, fetching past robot trajectories or motor skills to facilitate few-shot imitation."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=R79BKRR9) 
  
 <mark class="hltr-yellow">"Others, such as SayComply [6], focus on constraint retrieval, querying text-based safety manuals to ensure operational compliance."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=LS3BNNX3) 
  
 <mark class="hltr-orange">"owever, they rely on the assumption that the task has either been demonstrated before or can be solved through high-level textual constraints."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=LFZ683TA) 
  
 <mark class="hltr-orange">"How can a robot solve a strictly zero-shot manipulation task where no prior trajectory exists, but explicit procedural instructions are available?"</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=I64KLBVN) 
  
 <mark class="hltr-yellow">"we introduce a framework for document-driven robotic planning, treating the robot as an information-seeking agent that closes the loop between visual retrieval and physical actuation."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=4K7AGSP3) 
  
 <mark class="hltr-yellow">"Unlike traditional Retrieval-Augmented Generation (RAG) systems [8, 17, 22] that retrieve text to generate answers, our approach retrieves visual assembly manuals to generate actions."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=62KR5JPA) 
  
 <mark class="hltr-yellow">"Retrieve-Reason-Act loop."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=45YKZJJY) 
  
 <mark class="hltr-yellow">"We validate this approach on the IKEA Furniture Assembly benchmark [14], a challenging domain that requires precise interpretation of multi-step visual instructions."</mark> [Page 1](zotero://open-pdf/library/items/YUHWDBTK?page=1&annotation=P33IIHPH) 
  
 <mark class="hltr-yellow">"Retrieval as a Control Primitive: Augmenting the planner with exact visual manuals improves task success rates by over 20% compared to standard VLM baselines."</mark> [Page 2](zotero://open-pdf/library/items/YUHWDBTK?page=2&annotation=PMSIASVN) 
  
 <mark class="hltr-yellow">"Visual Grounding is Key: We identify that the primary bottleneck in embodied RAG is not the retrieval of documents, but the cross-modal alignment between 2D diagrams and 3D physical parts."</mark> [Page 2](zotero://open-pdf/library/items/YUHWDBTK?page=2&annotation=5X6BREJ8) 
  
 <mark class="hltr-yellow">"Instruction vs. Imitation: We provide empirical evidence that for complex, long-horizon tasks, retrieving procedural instructions (our method) is more effective than retrieving semantically similar but structurally different past examples."</mark> [Page 2](zotero://open-pdf/library/items/YUHWDBTK?page=2&annotation=MHBNYC7X) 
  
 <mark class="hltr-purple">"2 RELATED WORK"</mark> [Page 2](zotero://open-pdf/library/items/YUHWDBTK?page=2&annotation=UJ7GJ6RI) 
  
 <mark class="hltr-purple">"2.1 Experience Retrieval: RAG for Motor Skills"</mark> [Page 2](zotero://open-pdf/library/items/YUHWDBTK?page=2&annotation=5MJ4N2BC) 
  
 <mark class="hltr-purple">"2.2 Constraint Retrieval: RAG for Governance"</mark> [Page 2](zotero://open-pdf/library/items/YUHWDBTK?page=2&annotation=NLTA92I8) 
  
 <mark class="hltr-purple">"2.3 Visual RAG and Document-Grounded Control"</mark> [Page 2](zotero://open-pdf/library/items/YUHWDBTK?page=2&annotation=5CVMM2ZR) 
  
 <mark class="hltr-purple">"3 METHODOLOGY"</mark> [Page 2](zotero://open-pdf/library/items/YUHWDBTK?page=2&annotation=ZCP5SMVI) 
  
 <mark class="hltr-purple">"3.1 Dataset"</mark> [Page 2](zotero://open-pdf/library/items/YUHWDBTK?page=2&annotation=5YK6E6YB) 
  
 <mark class="hltr-purple">"3.1.1 Data Preprocessing."</mark> [Page 3](zotero://open-pdf/library/items/YUHWDBTK?page=3&annotation=L598CDNC) 
  
 <mark class="hltr-purple">"3.1.2 Ground Truth Label Extraction."</mark> [Page 3](zotero://open-pdf/library/items/YUHWDBTK?page=3&annotation=TT8Y6ZK5) 
  
 <mark class="hltr-purple">"3.1.3 Dataset Statistics."</mark> [Page 3](zotero://open-pdf/library/items/YUHWDBTK?page=3&annotation=DR2HC247) 
  
 <mark class="hltr-purple">"3.2 Framework"</mark> [Page 3](zotero://open-pdf/library/items/YUHWDBTK?page=3&annotation=EWKLPF8B) 
  
 <mark class="hltr-purple">"3.2.1 Baseline Information."</mark> [Page 3](zotero://open-pdf/library/items/YUHWDBTK?page=3&annotation=92Y993CW) 
  
 <mark class="hltr-purple">"3.2.2 Retrieval Methods."</mark> [Page 4](zotero://open-pdf/library/items/YUHWDBTK?page=4&annotation=TME5GRL5) 
  
 <mark class="hltr-purple">"3.2.3 Prediction Methods."</mark> [Page 4](zotero://open-pdf/library/items/YUHWDBTK?page=4&annotation=57LHCZC4) 
  
 <mark class="hltr-purple">"3.2.4 Language Model."</mark> [Page 5](zotero://open-pdf/library/items/YUHWDBTK?page=5&annotation=TH2ZD5IS) 
  
 <mark class="hltr-purple">"4 EXPERIMENTS"</mark> [Page 5](zotero://open-pdf/library/items/YUHWDBTK?page=5&annotation=NRAAE4TN) 
  
 <mark class="hltr-purple">"4.1 Experimental Setup"</mark> [Page 5](zotero://open-pdf/library/items/YUHWDBTK?page=5&annotation=8ERLTLWE) 
  
 <mark class="hltr-purple">"4.1.1 Evaluation Metrics."</mark> [Page 5](zotero://open-pdf/library/items/YUHWDBTK?page=5&annotation=WQNP3L6C) 
  
 <mark class="hltr-purple">"4.1.2 Implementation Details."</mark> [Page 5](zotero://open-pdf/library/items/YUHWDBTK?page=5&annotation=MCHSKSFS) 
  
 <mark class="hltr-purple">"4.2 Main Results"</mark> [Page 5](zotero://open-pdf/library/items/YUHWDBTK?page=5&annotation=K4XP5H5R) 
  
 <mark class="hltr-purple">"4.2.1 Key Findings."</mark> [Page 5](zotero://open-pdf/library/items/YUHWDBTK?page=5&annotation=ZU4VQMME) 
  
 <mark class="hltr-purple">"4.3 Analysis by Task Characteristics"</mark> [Page 6](zotero://open-pdf/library/items/YUHWDBTK?page=6&annotation=JC5WQ85B) 
  
 <mark class="hltr-purple">"4.3.1 Performance by Complexity."</mark> [Page 6](zotero://open-pdf/library/items/YUHWDBTK?page=6&annotation=AWEV2ECQ) 
  
 <mark class="hltr-purple">"4.3.2 Performance by Category."</mark> [Page 6](zotero://open-pdf/library/items/YUHWDBTK?page=6&annotation=4ZAT89CF) 
  
 <mark class="hltr-purple">"4.4 Error Analysis"</mark> [Page 7](zotero://open-pdf/library/items/YUHWDBTK?page=7&annotation=L5SXU23L) 
  
 <mark class="hltr-purple">"4.5 Ablation Studies"</mark> [Page 7](zotero://open-pdf/library/items/YUHWDBTK?page=7&annotation=MWCQJZ9Z) 
  
 <mark class="hltr-purple">"4.5.1 Effect of Retrieved Example Count (k)."</mark> [Page 7](zotero://open-pdf/library/items/YUHWDBTK?page=7&annotation=26EXA3X6) 
  
 <mark class="hltr-purple">"4.5.2 Impact of Retrieval Strategy."</mark> [Page 7](zotero://open-pdf/library/items/YUHWDBTK?page=7&annotation=D7PIELMU) 
  
 <mark class="hltr-purple">"4.6 Robotic Execution"</mark> [Page 8](zotero://open-pdf/library/items/YUHWDBTK?page=8&annotation=A9DJRZJL) 
  
 <mark class="hltr-purple">"4.6.1 Simulation Setup."</mark> [Page 8](zotero://open-pdf/library/items/YUHWDBTK?page=8&annotation=HBA4TJCV) 
  
 <mark class="hltr-purple">"4.6.2 Retrieve-Reason-Act Loop."</mark> [Page 8](zotero://open-pdf/library/items/YUHWDBTK?page=8&annotation=LEEDB56D) 
  
 <mark class="hltr-purple">"4.6.3 Execution Results."</mark> [Page 8](zotero://open-pdf/library/items/YUHWDBTK?page=8&annotation=Q559W4AQ) 
  
 <mark class="hltr-purple">"5 DISCUSSION"</mark> [Page 8](zotero://open-pdf/library/items/YUHWDBTK?page=8&annotation=BFZHIN3W) 
  
 <mark class="hltr-purple">"5.1 What Does Retrieval Enable in Robotic Control?"</mark> [Page 8](zotero://open-pdf/library/items/YUHWDBTK?page=8&annotation=RHRP8UB3) 
  
 <mark class="hltr-purple">"5.2 Why Does Performance Saturate Despite Perfect Retrieval?"</mark> [Page 9](zotero://open-pdf/library/items/YUHWDBTK?page=9&annotation=Q37WEDRN) 
  
 <mark class="hltr-purple">"5.3 Implications for Information Retrieval"</mark> [Page 9](zotero://open-pdf/library/items/YUHWDBTK?page=9&annotation=BWN4I4W8) 
  
 <mark class="hltr-purple">"6 CONCLUSION"</mark> [Page 9](zotero://open-pdf/library/items/YUHWDBTK?page=9&annotation=J4K8536V) 
  
 <mark class="hltr-yellow">"(4) End-to-End Simulation: We demonstrate the complete pipeline from document retrieval to assembly execution in NVIDIA Isaac Sim, showing that retrieval-augmented reasoning can directly drive simulated robot behavior."</mark> [Page 9](zotero://open-pdf/library/items/YUHWDBTK?page=9&annotation=DQNZ6FV7) 
  
 <mark class="hltr-yellow">"Task complexity (number of parts) is the primary performance bottleneck."</mark> [Page 9](zotero://open-pdf/library/items/YUHWDBTK?page=9&annotation=EG3XF7EW) 
  
 <mark class="hltr-yellow">"systematic underprediction rather than hallucination—predicting 743 connections versus 1,131 ground truth—suggesting that visual procedural understanding, not retrieval quality, is the key challenge for future work."</mark> [Page 9](zotero://open-pdf/library/items/YUHWDBTK?page=9&annotation=QMBC4VYC) 
  
 <mark class="hltr-orange">"(1) improving visual instruction following for complex multipart assemblies through specialized architectural components"</mark> [Page 9](zotero://open-pdf/library/items/YUHWDBTK?page=9&annotation=CT6I8FI3) 
  
 <mark class="hltr-orange">"(2) extending the framework to other procedural domains such as manufacturing, cooking, and medical procedures where visual instructions guide physical actions."</mark> [Page 9](zotero://open-pdf/library/items/YUHWDBTK?page=9&annotation=THELM5G7) 
  
