---
title: "[[$π_{0.5}$ - a Vision-Language-Action Model with Open-World Generalization]]"
year: 2025 
authors: Physical Intelligence, Kevin Black, Noah Brown, James Darpinian, Karan Dhabalia, Danny Driess, Adnan Esmail, Michael Equi, Chelsea Finn, Niccolo Fusai, Manuel Y. Galliker, Dibya Ghosh, Lachy Groom, Karol Hausman, Brian Ichter, Szymon Jakubczak, Tim Jones, Liyiming Ke, Devin LeBlanc, Sergey Levine, Adrian Li-Bell, Mohith Mothukuri, Suraj Nair, Karl Pertsch, Allen Z. Ren, Lucy Xiaoyang Shi, Laura Smith, Jost Tobias Springenberg, Kyle Stachowicz, James Tanner, Quan Vuong, Homer Walke, Anna Walling, Haohuan Wang, Lili Yu, Ury Zhilinsky
categories:
  - "[[Research References]]"
tags: 
- Computer-Science---Machine-Learning 
- Computer-Science---Robotics 
- first 
---

Zotero PDF Link: [[Zotero Attachments/Intelligence et al. - 2025 - $π_{0.5}$ a Vision-Language-Action Model with Open-World Generalization.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"Abstract"</mark> [Page 1](zotero://open-pdf/library/items/UQYID9KF?page=1&annotation=FPWU875M) 
  
 <mark class="hltr-yellow">"π0.5, a new model based on π0 that uses co-training on heterogeneous tasks to enable broad generalization"</mark> [Page 1](zotero://open-pdf/library/items/UQYID9KF?page=1&annotation=GQVCIQH3) 
  
 <mark class="hltr-purple">"I. INTRODUCTION"</mark> [Page 1](zotero://open-pdf/library/items/UQYID9KF?page=1&annotation=6647IXPD) 
  
 <mark class="hltr-yellow">"by casting different modalities into the same sequence modeling framework, VLAs can be adapted to train on robot data, language data, computer vision tasks, and combinations of the above."</mark> [Page 2](zotero://open-pdf/library/items/UQYID9KF?page=2&annotation=2Y9BREQ6) 
  
 <mark class="hltr-yellow">"utilize heterogeneous and diverse knowledge sources to enable broad generalization."</mark> [Page 2](zotero://open-pdf/library/items/UQYID9KF?page=2&annotation=DGRR58GE) 
  
 <mark class="hltr-yellow">"which can control mobile manipulators to perform a variety of household tasks even in homes that were never seen during training."</mark> [Page 2](zotero://open-pdf/library/items/UQYID9KF?page=2&annotation=7LLBYPJH) 
  
 <mark class="hltr-yellow">"draws on experience from many sources: in addition to a medium-sized dataset collected directly with mobile manipulators in a variety of real homes (about 400 hours), π0.5 uses data from other non-mobile robots, data of related tasks collected under laboratory conditions, training examples that require predicting “high-level” semantic tasks based on robot observation, verbal language instructions provided to the robot by human supervisors, and a variety of multi-modal examples created from web data, such as image captioning, question answering, and object localization"</mark> [Page 2](zotero://open-pdf/library/items/UQYID9KF?page=2&annotation=K2BFAATE) 
  
 <mark class="hltr-yellow">"design of π0.5 follows a simple hierarchical architecture"</mark> [Page 2](zotero://open-pdf/library/items/UQYID9KF?page=2&annotation=BBXVE3RD) 
  
 <mark class="hltr-yellow">"first pre-train the model on the heterogeneous mixture of training tasks"</mark> [Page 2](zotero://open-pdf/library/items/UQYID9KF?page=2&annotation=28TFCC72) 
  
 <mark class="hltr-yellow">"then fine-tune it specifically for mobile manipulation with both low-level action examples and high-level “semantic” actions"</mark> [Page 2](zotero://open-pdf/library/items/UQYID9KF?page=2&annotation=AHI7DIEP) 
  
 <mark class="hltr-yellow">"At runtime, during each step of inference, the model first predicts the semantic subtask, inferring the behavior that is appropriate to perform next based on the task structure and the semantics of the scene, and then predicts the low-level robot action chunk based on this subtask."</mark> [Page 2](zotero://open-pdf/library/items/UQYID9KF?page=2&annotation=L5EKK2HC) 
  
 <mark class="hltr-yellow">"the low-level action inference procedure readily benefits from action data collected by other robots"</mark> [Page 2](zotero://open-pdf/library/items/UQYID9KF?page=2&annotation=IXJH4RB4) 
  
 <mark class="hltr-yellow">"the high-level inference procedure benefits from semantic examples from the web, high-level annotation prediction, and even verbal commands"</mark> [Page 2](zotero://open-pdf/library/items/UQYID9KF?page=2&annotation=VGCJ7KWL) 
  
 <mark class="hltr-purple">"II. RELATED WORK"</mark> [Page 3](zotero://open-pdf/library/items/UQYID9KF?page=3&annotation=ARPZHTXE) 
  
 <mark class="hltr-purple">"III. PRELIMINARIES"</mark> [Page 4](zotero://open-pdf/library/items/UQYID9KF?page=4&annotation=D89RSZVF) 
  
 <mark class="hltr-yellow">"Vision-language-action models (VLAs) are typically trained via imitation learning"</mark> [Page 4](zotero://open-pdf/library/items/UQYID9KF?page=4&annotation=FPRPWUTP) 
  
 <mark class="hltr-yellow">"by maximizing the log-likelihood of an action at (or, more generally, an action chunk at:t+H ) given an observation ot and a natural language task instruction l: maxθ E(at:t+H ,ot,l)∼D log πθ(at:t+H |ot, l) ."</mark> [Page 4](zotero://open-pdf/library/items/UQYID9KF?page=4&annotation=W72AWHKJ) 
  
 <mark class="hltr-yellow">"observation  typically contains one or more images It1, ..., Itn and proprioceptive state qt, which captures the position of the robot’s joints."</mark> [Page 4](zotero://open-pdf/library/items/UQYID9KF?page=4&annotation=6HE8WQLM) 
  
 <mark class="hltr-yellow">"VLA architectures follow the design of modern language and vision-language models, with modality-specific tokenizers that map inputs and outputs to discrete (“hard”) or continuous (“soft”) token representations, and a large, autoregressive transformer backbone that is trained to map from  input to output tokens."</mark> [Page 4](zotero://open-pdf/library/items/UQYID9KF?page=4&annotation=JQ27G8D2) 
  
 <mark class="hltr-yellow">"By encoding policy inputs and outputs into tokenized representations, the imitation learning problem described above can be cast as a simple next-token-prediction problem over a sequence of observation, instruction and action tokens"</mark> [Page 4](zotero://open-pdf/library/items/UQYID9KF?page=4&annotation=BC6DY54P) 
  
 <mark class="hltr-yellow">"For actions, prior work has developed effective, compressionbased tokenization approaches [64], which we use in this work during pretraining."</mark> [Page 4](zotero://open-pdf/library/items/UQYID9KF?page=4&annotation=WMV4BVH8) 
  
 <mark class="hltr-yellow">"During the post-training phase of our model, we will build on the design of the π0 model [8], which represents the action distribution via flow matching."</mark> [Page 4](zotero://open-pdf/library/items/UQYID9KF?page=4&annotation=Q5YYVY5K) 
  
 <mark class="hltr-yellow">"These tokens also use a different set of model weights, which we refer to as an “action expert,” analogously to a mixture of experts architecture"</mark> [Page 4](zotero://open-pdf/library/items/UQYID9KF?page=4&annotation=XAXFHUF7) 
  
 <mark class="hltr-purple">"IV. THE π0.5 MODEL AND TRAINING RECIPE"</mark> [Page 4](zotero://open-pdf/library/items/UQYID9KF?page=4&annotation=2ZIBVSUK) 
  
 <mark class="hltr-purple">"A. The π0.5 architecture"</mark> [Page 5](zotero://open-pdf/library/items/UQYID9KF?page=5&annotation=XEP6SP5B) 
  
 <mark class="hltr-purple">"B. Combining discrete & continuous action representations"</mark> [Page 5](zotero://open-pdf/library/items/UQYID9KF?page=5&annotation=FDIYSMTF) 
  
 <mark class="hltr-purple">"C. Pre-training"</mark> [Page 6](zotero://open-pdf/library/items/UQYID9KF?page=6&annotation=VXXLJJW9) 
  
 <mark class="hltr-purple">"D. Post-training"</mark> [Page 7](zotero://open-pdf/library/items/UQYID9KF?page=7&annotation=EETY3PDY) 
  
 <mark class="hltr-purple">"E. Robot system details"</mark> [Page 7](zotero://open-pdf/library/items/UQYID9KF?page=7&annotation=473HI4ZD) 
  
 <mark class="hltr-purple">"V. EXPERIMENTAL EVALUATION"</mark> [Page 7](zotero://open-pdf/library/items/UQYID9KF?page=7&annotation=DKUAGWLU) 
  
 <mark class="hltr-purple">"A. Can π0.5 generalize to real homes?"</mark> [Page 7](zotero://open-pdf/library/items/UQYID9KF?page=7&annotation=V5DP4SSQ) 
  
 <mark class="hltr-purple">"B. How does generalization scale with the number of scenes?"</mark> [Page 8](zotero://open-pdf/library/items/UQYID9KF?page=8&annotation=43GUJ38R) 
  
 <mark class="hltr-purple">"C. How important is each part of our co-training recipe?"</mark> [Page 9](zotero://open-pdf/library/items/UQYID9KF?page=9&annotation=XFU9WVX8) 
  
 <mark class="hltr-purple">"D. How does π0.5 compare to other VLAs?"</mark> [Page 10](zotero://open-pdf/library/items/UQYID9KF?page=10&annotation=3AJVADLL) 
  
 <mark class="hltr-purple">"E. How important is high-level inference?"</mark> [Page 10](zotero://open-pdf/library/items/UQYID9KF?page=10&annotation=SZ2B5UNL) 
  
 <mark class="hltr-purple">"VI. DISCUSSION AND FUTURE WORK"</mark> [Page 11](zotero://open-pdf/library/items/UQYID9KF?page=11&annotation=M6IYKLUQ) 
  
 <mark class="hltr-yellow">"Some environments present persistent challenges (e.g., unfamiliar handles on drawers, or cabinets that are physically hard for the robot to open), some behaviors present challenges with partial observability (e.g., the robot arm occluding a spill that should be wiped), and in some cases the high-level subtask inference is easily distracted (e.g., closing and opening a drawer multiple times while putting away items)."</mark> [Page 11](zotero://open-pdf/library/items/UQYID9KF?page=11&annotation=SG73USLF) 
  
 <mark class="hltr-yellow">"The complexity of the prompts that the model can accommodate is determined by the training data, and more complex preferences and instructions could be incorporated by producing more intricate and diverse annotations, either with human labelers or synthetically."</mark> [Page 11](zotero://open-pdf/library/items/UQYID9KF?page=11&annotation=VZZQVDLD) 
  
 <mark class="hltr-purple">"B. Task evaluation rubric"</mark> [Page 17](zotero://open-pdf/library/items/UQYID9KF?page=17&annotation=G8RAGTKX) 
  
 <mark class="hltr-purple">"C. Language following experiment setup"</mark> [Page 17](zotero://open-pdf/library/items/UQYID9KF?page=17&annotation=BBTDCC4D) 
  
 <mark class="hltr-purple">"E. Model technical details"</mark> [Page 19](zotero://open-pdf/library/items/UQYID9KF?page=19&annotation=74PBRKDH) 
  
