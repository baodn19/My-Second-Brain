---
title: "[[Terra - Hierarchical Terrain-Aware 3D Scene Graph for Task-Agnostic Outdoor Mapping]]"
year: 2025 
authors: Chad R. Samuelson, Abigail Austin, Seth Knoop, Blake Romrell, Gabriel R. Slade, Timothy W. McLain, Joshua G. Mangelson
categories:
  - "[[Research References]]"
tags: 
- Computer-Science---Robotics 
---

Zotero PDF Link: [[Zotero Attachments/Samuelson et al. - 2025 - Terra Hierarchical Terrain-Aware 3D Scene Graph for Task-Agnostic Outdoor Mapping.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"Abstract"</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=8H6FBRA2) 
  
 <mark class="hltr-orange">"Classical geometric mapping methods retain essential structural environment information, but lack a semantic understanding and organization to allow high-level robotic reasoning."</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=LTT4LSWB) 
  
 <mark class="hltr-yellow">"3D scene graphs (3DSGs) address this limitation by integrating geometric, topological, and semantic relationships into a multi-level graph-based map."</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=3KMLZGCP) 
  
 <mark class="hltr-purple">"I. INTRODUCTION"</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=ASEDQ9CQ) 
  
 <mark class="hltr-yellow">"LiDAR has become a standard sensor for large-scale outdoor geometric mapping [1–3]. Beyond geometry, some approaches train models to semantically classify points in LiDAR scans"</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=UKR67GUY) 
  
 <mark class="hltr-orange">"While promising, these models are still largely closed-set (restricted to a fixed set of semantic classes)."</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=9CDHWG2U) 
  
 <mark class="hltr-yellow">"Cameras, in contrast, provide rich visual data and have achieved remarkable success in semantic scene under"</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=EQIACNG2) 
  
 <mark class="hltr-yellow">"standing. Recent techniques enable more general open-set scene understanding and even enable grounding of visual data with natural language through vision-language models (VLMs)"</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=IB66GPF8) 
  
 <mark class="hltr-yellow">"Many 3DSGbased methods utilize VLMs and large language models (LLMs) for both scene graph construction and autonomous task planning."</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=83FF4ELR) 
  
 <mark class="hltr-yellow">"3DSG methods focus on indoor environments using camera imagery and depth data to build a semantically-classified mesh that forms the base layer of the 3DSG"</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=P83RCHDN) 
  
 <mark class="hltr-orange">"constructing mesh maps over large areas is both computationally and memory intensive"</mark> [Page 1](zotero://open-pdf/library/items/PJDGE84N?page=1&annotation=QKY2D6GS) 
  
 <mark class="hltr-orange">"camera-derived depth has limited range (≤ 20 meters). These both restrict indoor 3DSG techniques from scaling to large outdoor settings."</mark> [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=X9F7ECLR) 
  
 <mark class="hltr-yellow">"combine indoor 3DSG techniques with geometrically robust outdoor LiDAR SLAM methods, enabling metric-semantic mapping in large-scale outdoor environments, we term our method Terra"</mark> [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=CFBT5CNP) 
  
 <mark class="hltr-yellow">"A novel, memory-efficient, and task-agnostic approach for open-set metric-semantic mapping in large-scale outdoor environments,"</mark> [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=U5N2XQE8) 
 
Does the paper test on edge devices [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=U5N2XQE8) 
  
 <mark class="hltr-yellow">"A terrain layer in the outdoor 3DSG that supports terrain-aware tasks where VLMs alone struggle"</mark> [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=KXVDUF69) 
  
 <mark class="hltr-yellow">"Hierarchical region layers to handle multiple levels of task abstraction"</mark> [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=7WCCR2B7) 
  
 <mark class="hltr-yellow">"in-depth evaluation on simulated and real world data comparing Terra with state-of-the-art (SOTA) indoor 3DSG methods"</mark> [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=ZQWJSMNR) 
 
why not compare with SOTA outdoor method [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=ZQWJSMNR) 
  
 <mark class="hltr-purple">"II. RELATED WORK"</mark> [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=YPJ4KGDE) 
  
 <mark class="hltr-purple">"A. LiDAR Mapping and Semantics"</mark> [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=LWKZS6X4) 
  
 <mark class="hltr-purple">"B. Indoor 3D Scene Graphs"</mark> [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=EQULGQML) 
  
 <mark class="hltr-purple">"C. Outdoor 3D Scene Graphs"</mark> [Page 2](zotero://open-pdf/library/items/PJDGE84N?page=2&annotation=AVWSWCKA) 
  
 <mark class="hltr-purple">"III. TERRA: HIERARCHICAL TERRAIN-AWARE 3D SCENE  GRAPHS FOR TASK-AGNOSTIC OUTDOOR MAPPING"</mark> [Page 3](zotero://open-pdf/library/items/PJDGE84N?page=3&annotation=YJFY9LFL) 
  
 <mark class="hltr-purple">"A. Phase 1: Task-Agnostic Metric-Semantic Mapping"</mark> [Page 3](zotero://open-pdf/library/items/PJDGE84N?page=3&annotation=LCDBNPYV) 
  
 <mark class="hltr-purple">"B. Phase 2: Task-Agnostic 3DSG Construction"</mark> [Page 4](zotero://open-pdf/library/items/PJDGE84N?page=4&annotation=8G7J3PTK) 
  
 <mark class="hltr-purple">"C. Phase 3: Task-Driven 3DSG Querying and Navigation"</mark> [Page 5](zotero://open-pdf/library/items/PJDGE84N?page=5&annotation=WVY8WYTD) 
  
 <mark class="hltr-purple">"D. Platform details"</mark> [Page 5](zotero://open-pdf/library/items/PJDGE84N?page=5&annotation=CMGH2IZN) 
  
 <mark class="hltr-purple">"IV. EXPERIMENTS"</mark> [Page 5](zotero://open-pdf/library/items/PJDGE84N?page=5&annotation=Y22HL3WS) 
  
 <mark class="hltr-purple">"A. Datasets"</mark> [Page 5](zotero://open-pdf/library/items/PJDGE84N?page=5&annotation=AR4IFIYM) 
  
 <mark class="hltr-purple">"B. 2D Terrain Classification"</mark> [Page 5](zotero://open-pdf/library/items/PJDGE84N?page=5&annotation=Y8VR7X3Y) 
  
 <mark class="hltr-purple">"C. Open-set 3D Object Retrieval"</mark> [Page 6](zotero://open-pdf/library/items/PJDGE84N?page=6&annotation=MAY6J8K9) 
  
 <mark class="hltr-purple">"D. Hierarchical Region Evaluation"</mark> [Page 7](zotero://open-pdf/library/items/PJDGE84N?page=7&annotation=8PDXA75Y) 
  
 <mark class="hltr-purple">"E. Navigation"</mark> [Page 7](zotero://open-pdf/library/items/PJDGE84N?page=7&annotation=65PII2UK) 
  
 <mark class="hltr-purple">"V. CONCLUSION"</mark> [Page 7](zotero://open-pdf/library/items/PJDGE84N?page=7&annotation=2LPVULPC) 
  
 <mark class="hltr-yellow">"extending this method into a full realtime pipeline and exploring more robust 3DSG techniques for off-road and complex natural environments."</mark> [Page 7](zotero://open-pdf/library/items/PJDGE84N?page=7&annotation=T3GKE469) 
  
 <mark class="hltr-orange">"we leverage CLIP for its efficiency, compact size, and taskagnostic open-set embeddings, its reliance on prompt-tuning and view-dependent recognition remain limitations, which future LLM-based VLMs may help overcome."</mark> [Page 7](zotero://open-pdf/library/items/PJDGE84N?page=7&annotation=YBIEIFM2) 
  
 <mark class="hltr-yellow">"[1] T. Shan and B. Englot, “LeGO-LOAM: Lightweight and groundoptimized lidar odometry and mapping on variable terrain,” in Proc. of the IEEE Intl. Conf. on Intelligent Robots and Systems (IROS), 2018"</mark> [Page 7](zotero://open-pdf/library/items/PJDGE84N?page=7&annotation=L9AQ6TKJ) 
  
