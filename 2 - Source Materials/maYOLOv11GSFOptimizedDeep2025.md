---
title: "[[YOLOv11-GSF - an optimized deep learning model for strawberry ripeness detection in agriculture]]"
year: 2025
authors: Haoran Ma, Qian Zhao, Runqing Zhang, Chunxu Hao, Wenhui Dong, Xiaoying Zhang, Fuzhong Li, Xiaoqin Xue, Gongqing Sun
categories:
  - "[[Research References]]"
tags:
  - C3K2-SG-module
  - F-PIoUv2-loss-function
  - ghost-module
  - object-detection
  - strawberry
  - YOLOv11
pass:
  - first
modified: February 14th 2026, 5:43:19 pm
---

Zotero PDF Link: [[Zotero Attachments/Ma et al. - 2025 - YOLOv11-GSF an optimized deep learning model for strawberry ripeness detection in agriculture.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-orange">"dense clusters of strawberries, frequent occlusions, overlaps, and fluctuating lighting conditions, presents significant hurdles for existing detection methodologies. These methods often suffer from low efficiency, high computational expenses, and subpar accuracy in scenarios involving small and densely packed targets"</mark> [Page 1](zotero://open-pdf/library/items/V6HRNXDA?page=1&annotation=9D5XRCFN) 
  
 <mark class="hltr-yellow">"YOLOv11-GSF, a real-time strawberry ripeness detection algorithm based on YOLOv11, which incorporates several innovative features: a Ghost Convolution (GhostConv) convolution method"</mark> [Page 1](zotero://open-pdf/library/items/V6HRNXDA?page=1&annotation=LBPEZH57) 
  
 <mark class="hltr-yellow">"a C3K2SG module that combines self-moving point convolution (SMPConv) and convolutional gated linear units (CGLU)"</mark> [Page 1](zotero://open-pdf/library/items/V6HRNXDA?page=1&annotation=6PYPDCJD) 
  
 <mark class="hltr-yellow">"F-PIoUv2 loss function inspired by Focaler IoU and PIoUv2"</mark> [Page 1](zotero://open-pdf/library/items/V6HRNXDA?page=1&annotation=IUYZHWAP) 
  
 <mark class="hltr-yellow">"superior performance of YOLOv11-GSF, achieving an average precision of 97.8%, an accuracy of 95.99%, and a recall rate of 93.62%, representing improvements of 1.8%, 1.3 percentage points, and 2.1% over the original YOLOv11"</mark> [Page 1](zotero://open-pdf/library/items/V6HRNXDA?page=1&annotation=FTD7LLJL) 
  
 <mark class="hltr-purple">"1 Introduction"</mark> [Page 2](zotero://open-pdf/library/items/V6HRNXDA?page=2&annotation=7AZULCEL) 
  
 <mark class="hltr-green">"Preharvest yield assessment is a crucial link in strawberry cultivation management, providing vital data support for sales plan formulation and fertilizer application schemes for the next season."</mark> [Page 2](zotero://open-pdf/library/items/V6HRNXDA?page=2&annotation=QFCJXJ5Q) 
  
 <mark class="hltr-yellow">"In the context of smart agriculture, maturity detection technologies based on image recognition and deep learning have gradually gained widespread attention and application."</mark> [Page 2](zotero://open-pdf/library/items/V6HRNXDA?page=2&annotation=PQZBB87U) 
 
Look into maturity detection [Page 2](zotero://open-pdf/library/items/V6HRNXDA?page=2&annotation=PQZBB87U) 
  
 <mark class="hltr-green">"The rapid advancement of machine vision and deep learning technologies has led to the increasing maturity of target detection applications in agriculture (Xu et al., 2022)."</mark> [Page 2](zotero://open-pdf/library/items/V6HRNXDA?page=2&annotation=VU2JTSCR) 
  
 <mark class="hltr-gray">"(Xu et al., 2022)"</mark> [Page 2](zotero://open-pdf/library/items/V6HRNXDA?page=2&annotation=4DC7MJPB) 
  
 <mark class="hltr-yellow">"improved YOLOv5 target detection algorithm based on the GAM(Global Attention Mechanism) attention mechanism, enhancing the model’s feature extraction capability by adding the GAM attention mechanism"</mark> [Page 2](zotero://open-pdf/library/items/V6HRNXDA?page=2&annotation=DBK5488X) 
  
 <mark class="hltr-yellow">"Gong et al. (2024) designed a strawberry picking robot capable of precise recognition and localization of strawberries, with a recognition rate of 95% for ripe strawberries."</mark> [Page 2](zotero://open-pdf/library/items/V6HRNXDA?page=2&annotation=P5AMCVQ8) 
  
 <mark class="hltr-yellow">"Tang et al. (2023) proposed an improved YOLOv7-Tiny model for ripe strawberry recognition."</mark> [Page 2](zotero://open-pdf/library/items/V6HRNXDA?page=2&annotation=VUPDVV33) 
  
 <mark class="hltr-yellow">"Yang et al. (2024) proposed a strawberry recognition and localization method combining an improved YOLOv8 algorithm with a pose keypoint detection algorithm"</mark> [Page 2](zotero://open-pdf/library/items/V6HRNXDA?page=2&annotation=AZHSTU7B) 
  
 <mark class="hltr-purple">"2 Materials and methods"</mark> [Page 3](zotero://open-pdf/library/items/V6HRNXDA?page=3&annotation=FIBTYCJC) 
  
 <mark class="hltr-purple">"2.1 Data collection"</mark> [Page 3](zotero://open-pdf/library/items/V6HRNXDA?page=3&annotation=3XHSZCI6) 
  
 <mark class="hltr-purple">"2.2 Data processing"</mark> [Page 3](zotero://open-pdf/library/items/V6HRNXDA?page=3&annotation=C9CKVNVT) 
  
 <mark class="hltr-purple">"2.3 Principle of YOLOv11"</mark> [Page 3](zotero://open-pdf/library/items/V6HRNXDA?page=3&annotation=4GNMYP75) 
  
 <mark class="hltr-purple">"2.4 Improvements to YOLOv11"</mark> [Page 4](zotero://open-pdf/library/items/V6HRNXDA?page=4&annotation=GN6QK6IW) 
  
 <mark class="hltr-purple">"2.4.1 GhostConv"</mark> [Page 4](zotero://open-pdf/library/items/V6HRNXDA?page=4&annotation=2YPT3H6H) 
  
 <mark class="hltr-purple">"2.4.2 C3k2-SG module"</mark> [Page 6](zotero://open-pdf/library/items/V6HRNXDA?page=6&annotation=VSVTFSHL) 
  
 <mark class="hltr-purple">"2.4.3 F-PIoUv2 loss function"</mark> [Page 8](zotero://open-pdf/library/items/V6HRNXDA?page=8&annotation=TFZUHXXU) 
  
 <mark class="hltr-purple">"3 Experimental design"</mark> [Page 10](zotero://open-pdf/library/items/V6HRNXDA?page=10&annotation=VYPNGQ4M) 
  
 <mark class="hltr-purple">"3.1 Experimental environment"</mark> [Page 10](zotero://open-pdf/library/items/V6HRNXDA?page=10&annotation=TRKL9PAT) 
  
 <mark class="hltr-purple">"3.2 Evaluation metrics"</mark> [Page 10](zotero://open-pdf/library/items/V6HRNXDA?page=10&annotation=4MZDWR75) 
  
 <mark class="hltr-purple">"4 Discussion"</mark> [Page 11](zotero://open-pdf/library/items/V6HRNXDA?page=11&annotation=QGNUHWGA) 
  
 <mark class="hltr-purple">"4.1 Comparison"</mark> [Page 11](zotero://open-pdf/library/items/V6HRNXDA?page=11&annotation=5CEPE64E) 
  
 <mark class="hltr-purple">"4.2 Ablation study"</mark> [Page 13](zotero://open-pdf/library/items/V6HRNXDA?page=13&annotation=PEUMEYPG) 
  
 <mark class="hltr-purple">"4.3 Visualization"</mark> [Page 14](zotero://open-pdf/library/items/V6HRNXDA?page=14&annotation=ZMK8CJ3Z) 
  
 <mark class="hltr-yellow">"The integration of GhostConv modules into the backbone network—replacing the fifth and seventh convolutional layersreduces computational complexity through dual-path feature generation."</mark> [Page 15](zotero://open-pdf/library/items/V6HRNXDA?page=15&annotation=IL8RLGSH) 
  
 <mark class="hltr-yellow">"The C3K2-SG module combines self-moving point convolution with adaptive gating mechanisms, enhancing feature extraction flexibility and precision."</mark> [Page 15](zotero://open-pdf/library/items/V6HRNXDA?page=15&annotation=SBENB3M2) 
  
 <mark class="hltr-yellow">"the F-PIoUv2 loss  function mitigates penalty factor amplification and class imbalance issues, collectively improving detection performance."</mark> [Page 15](zotero://open-pdf/library/items/V6HRNXDA?page=15&annotation=ZQF6PN3C) 
  
 <mark class="hltr-orange">"the model’s validation remains confined to image datasets, necessitating further real-world testing to ensure operational reliability."</mark> [Page 16](zotero://open-pdf/library/items/V6HRNXDA?page=16&annotation=CYSLC5BJ) 
  
 <mark class="hltr-yellow">"edge-device optimization for resource-constrained agricultural robots"</mark> [Page 16](zotero://open-pdf/library/items/V6HRNXDA?page=16&annotation=93Q7NY8K) 
 
aligns with ERA Lab [Page 16](zotero://open-pdf/library/items/V6HRNXDA?page=16&annotation=93Q7NY8K) 
  
 <mark class="hltr-yellow">"seamless integration with automated harvesting systems to enable closed-loop operations"</mark> [Page 16](zotero://open-pdf/library/items/V6HRNXDA?page=16&annotation=USG8FK4M) 
  
 <mark class="hltr-yellow">"cross-species adaptability studies to extend the model’s applicability to other small berry crops via transfer learning"</mark> [Page 16](zotero://open-pdf/library/items/V6HRNXDA?page=16&annotation=855K5CEJ) 
  
