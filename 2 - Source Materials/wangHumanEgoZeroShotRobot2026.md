---
title: "[[HumanEgo - Zero-Shot Robot Learning from Minutes of Human Egocentric Videos]]"
year: 2026 
authors: Zhi Wang, Botao He, Kelin Yu, Seungjae Lee, Ruohan Gao, Furong Huang, Yiannis Aloimonos
categories:
  - "[[Research References]]"
tags: 
---

Zotero PDF Link: [[Zotero Attachments/Wang et al. - 2026 - HumanEgo Zero-Shot Robot Learning from Minutes of Human Egocentric Videos.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"Abstract"</mark> [Page 1](zotero://open-pdf/library/items/87YUVSWH?page=1&annotation=5URH2CMN) 
  
 <mark class="hltr-purple">"1 Introduction"</mark> [Page 1](zotero://open-pdf/library/items/87YUVSWH?page=1&annotation=5DN4NAD6) 
  
 <mark class="hltr-yellow">"learning deployable manipulation policies from only minutes of human egocentric demonstrations—without any robot data and internet-scale pretraining."</mark> [Page 1](zotero://open-pdf/library/items/87YUVSWH?page=1&annotation=JDJVQR6I) 
  
 <mark class="hltr-yellow">"(1) The representation challenge: bridging the embodiment gap."</mark> [Page 1](zotero://open-pdf/library/items/87YUVSWH?page=1&annotation=ITU5FDKB) 
  
 <mark class="hltr-yellow">"We argue that neither hand nor object alone defines a skill—what matters is their interaction."</mark> [Page 2](zotero://open-pdf/library/items/87YUVSWH?page=2&annotation=8R27A7R6) 
  
 <mark class="hltr-yellow">"(2) The learning challenge: learning from minimal data."</mark> [Page 2](zotero://open-pdf/library/items/87YUVSWH?page=2&annotation=2JM2APTW) 
  
 <mark class="hltr-yellow">"This regime introduces two distinct challenges: multi-modality and signal sparsity."</mark> [Page 2](zotero://open-pdf/library/items/87YUVSWH?page=2&annotation=IGUF964C) 
  
 <mark class="hltr-yellow">"multi-modality challenge, the same task admits many valid strategies."</mark> [Page 2](zotero://open-pdf/library/items/87YUVSWH?page=2&annotation=J3AV8K34) 
  
 <mark class="hltr-yellow">"signal-sparsity challenge, each trajectory carries rich signal beyond the hand action—object motion, visual traces, hand–object state—yet prior work taps only a fraction: single auxiliary targets such as visual foresight [25, 29, 30] or 2D tracks [19, 27, 31], or upstream pretraining corpora [12, 13, 32]."</mark> [Page 2](zotero://open-pdf/library/items/87YUVSWH?page=2&annotation=2744UXCB) 
  
 <mark class="hltr-yellow">"For the visual gap, we inpaint the human arm from each egocentric frame and render a virtual gripper with tracked object keypoints in its place, producing an embodiment-agnostic visual observation."</mark> [Page 2](zotero://open-pdf/library/items/87YUVSWH?page=2&annotation=S769JTSF) 
  
 <mark class="hltr-yellow">"For the kinematic gap, we encode every hand and object as an Interaction-Centric Token (ICT), producing a compact, embodiment- and viewpoint-invariant spatial observation of hand–object interaction."</mark> [Page 2](zotero://open-pdf/library/items/87YUVSWH?page=2&annotation=XZDG86QH) 
  
 <mark class="hltr-yellow">"For multimodality, we adopt a flow matching [33] policy, producing expressive multi-modal actions at fast inference."</mark> [Page 2](zotero://open-pdf/library/items/87YUVSWH?page=2&annotation=I69YS6CW) 
  
 <mark class="hltr-yellow">"For signal sparsity, we design three dense auxiliary objectives: 2D trace, object motion, and latent consistency."</mark> [Page 2](zotero://open-pdf/library/items/87YUVSWH?page=2&annotation=3LCIXXR9) 
  
 <mark class="hltr-purple">"2 Related Work"</mark> [Page 2](zotero://open-pdf/library/items/87YUVSWH?page=2&annotation=E83KI3AR) 
  
 <mark class="hltr-purple">"3 HumanEgo"</mark> [Page 3](zotero://open-pdf/library/items/87YUVSWH?page=3&annotation=TMCK8CPR) 
  
 <mark class="hltr-purple">"3.1 Egocentric Data Collection"</mark> [Page 3](zotero://open-pdf/library/items/87YUVSWH?page=3&annotation=JUL8MPR9) 
  
 <mark class="hltr-purple">"3.2 Visual Observation Preprocessing"</mark> [Page 4](zotero://open-pdf/library/items/87YUVSWH?page=4&annotation=CFFVPSM4) 
  
 <mark class="hltr-purple">"3.3 Spatial Observation Preprocessing"</mark> [Page 4](zotero://open-pdf/library/items/87YUVSWH?page=4&annotation=5EI8VQSZ) 
  
 <mark class="hltr-purple">"3.4 Flow Matching Policy with Dense Auxiliary Objectives"</mark> [Page 4](zotero://open-pdf/library/items/87YUVSWH?page=4&annotation=M93RGEEC) 
  
 <mark class="hltr-purple">"4 Experiments"</mark> [Page 5](zotero://open-pdf/library/items/87YUVSWH?page=5&annotation=XSELKVRX) 
  
 <mark class="hltr-purple">"4.1 HumanEgo Bridges the Embodiment Gap Efficiently"</mark> [Page 5](zotero://open-pdf/library/items/87YUVSWH?page=5&annotation=AICJNGCY) 
  
 <mark class="hltr-purple">"4.2 The Efficiency of Human Demonstrations"</mark> [Page 6](zotero://open-pdf/library/items/87YUVSWH?page=6&annotation=DYFGMNUY) 
  
 <mark class="hltr-purple">"4.3 One Policy, Many Conditions"</mark> [Page 7](zotero://open-pdf/library/items/87YUVSWH?page=7&annotation=YTDHPYG9) 
  
 <mark class="hltr-purple">"4.4 What Drives Performance of HumanEgo?"</mark> [Page 7](zotero://open-pdf/library/items/87YUVSWH?page=7&annotation=L44Q7ULA) 
  
 <mark class="hltr-purple">"5 Conclusion"</mark> [Page 8](zotero://open-pdf/library/items/87YUVSWH?page=8&annotation=4AUIPP4A) 
  
 <mark class="hltr-yellow">"Our framework relies on Aria’s stereo hand tracking—monocular substitutes drop real-world success sharply (App. E.1), calling for stronger monocular hand pose estimators that recover absolute depth."</mark> [Page 8](zotero://open-pdf/library/items/87YUVSWH?page=8&annotation=GU5VRTWL) 
  
 <mark class="hltr-yellow">"The pipeline chains several off-the-shelf perception modules whose failures cascade into the policy, motivating stronger or jointly-trained frontends."</mark> [Page 8](zotero://open-pdf/library/items/87YUVSWH?page=8&annotation=YGY5FCJY) 
  
 <mark class="hltr-yellow">"few-shot learning plateaus at ∼1 cm precision; reaching sub-centimeter accuracy on contact-rich tasks will likely require reinforcement-learning refinement or simulation-based fine-tuning."</mark> [Page 8](zotero://open-pdf/library/items/87YUVSWH?page=8&annotation=PMZUBVNW) 
  
 <mark class="hltr-purple">"Appendix  A Data Collection Details  A.1 Aria Gen1 Glasses"</mark> [Page 15](zotero://open-pdf/library/items/87YUVSWH?page=15&annotation=GTYSAIXR) 
  
 <mark class="hltr-purple">"A.2 Task Details"</mark> [Page 15](zotero://open-pdf/library/items/87YUVSWH?page=15&annotation=GQMRDPTR) 
  
 <mark class="hltr-purple">"B Preprocessing Details  B.1 Triangulation"</mark> [Page 17](zotero://open-pdf/library/items/87YUVSWH?page=17&annotation=6RHRZVH8) 
  
 <mark class="hltr-purple">"B.2 Phase Detection"</mark> [Page 17](zotero://open-pdf/library/items/87YUVSWH?page=17&annotation=EKG6K4N5) 
  
 <mark class="hltr-purple">"B.3 Hand-to-Gripper Transfer"</mark> [Page 18](zotero://open-pdf/library/items/87YUVSWH?page=18&annotation=9AIZ3WZM) 
  
 <mark class="hltr-purple">"C Training Details  C.1 Flow Matching Policy"</mark> [Page 19](zotero://open-pdf/library/items/87YUVSWH?page=19&annotation=X5B3KH29) 
  
 <mark class="hltr-purple">"D Inference Details  D.1 Robot Inference Setup"</mark> [Page 20](zotero://open-pdf/library/items/87YUVSWH?page=20&annotation=M78WYWXD) 
  
 <mark class="hltr-yellow">"ACT baseline"</mark> [Page 20](zotero://open-pdf/library/items/87YUVSWH?page=20&annotation=ECCESF55) 
  
 <mark class="hltr-purple">"D.2 Flow Matching Rollout and Control"</mark> [Page 20](zotero://open-pdf/library/items/87YUVSWH?page=20&annotation=H27HVLAW) 
  
 <mark class="hltr-purple">"E Additional Experiments Analysis  E.1 Hand Tracking Method Study"</mark> [Page 21](zotero://open-pdf/library/items/87YUVSWH?page=21&annotation=WU98KTPN) 
  
 <mark class="hltr-purple">"E.2 Human-Robot Co-Training Study"</mark> [Page 22](zotero://open-pdf/library/items/87YUVSWH?page=22&annotation=N9F23IX2) 
  
 <mark class="hltr-purple">"E.3 Reference Frame Study"</mark> [Page 23](zotero://open-pdf/library/items/87YUVSWH?page=23&annotation=9BWQ33P8) 
  
 <mark class="hltr-purple">"F Hyperparameters"</mark> [Page 24](zotero://open-pdf/library/items/87YUVSWH?page=24&annotation=U4BV3LKU) 
  
