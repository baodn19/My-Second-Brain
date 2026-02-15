---
title: "[[Real-time lightweight strawberry ripeness detection framework based on YOLO11 deployed on edge computing platform]]"
year: 2025
authors: Yang Gan, Xuefeng Ren, Huan Liu, Yongming Chen, Ping Lin
categories:
  - "[[Research References]]"
tags:
  - Agricultural-environment
  - Edge-computing
  - Ripeness-detection
  - Strawberry
  - YOLO11
modified: February 15th 2026, 1:43:37 pm
---

Zotero PDF Link: [[Zotero Attachments/Gan et al. - 2025 - Real-time lightweight strawberry ripeness detection framework based on YOLO11 deployed on edge compu.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"Abstract"</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=8T8MZAQ4) 
  
 <mark class="hltr-orange">"Strawberry fruit detection, however, is often challenged by occlusions from stems and leaves, overlapping fruits, and complex background interference."</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=2HTYKXDH) 
  
 <mark class="hltr-yellow">"A compact module, termed the Pela block, is designed using partial convolution (PConv) to reduce parameter count and memory access, while simultaneously suppressing background interference"</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=V7YYKRTK) 
  
 <mark class="hltr-yellow">"A lightweight localization-based asymptotic feature pyramid network (LAFPN) is incorporated to enhance multi-scale detection performance"</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=K4CMI2TL) 
  
 <mark class="hltr-yellow">"a novel Focaler-PIoU loss function is introduced to direct the model toward anchor boxes of moderate quality, thereby mitigating the difficulty imbalance among strawberry samples"</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=QZ42VFJC) 
  
 <mark class="hltr-yellow">"large-scale, complex dataset is constructed, comprising 14,300 images and over 65,000 annotated strawberry instances, to evaluate the model."</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=W3VAAVV9) 
  
 <mark class="hltr-yellow">"When deployed on a Jetson AGX Orin embedded edge device with FP16 quantization, it sustains a detection speed of 90.1 FPS."</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=WMXYR3KN) 
  
 <mark class="hltr-purple">"Introduction"</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=TF7BDGWQ) 
  
 <mark class="hltr-green">"Strawberries are widely cultivated around the world due to their appealing flavor and high nutritional content, which has earned them the reputation of being the"Queen of Fruits"[1]."</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=N69U7U5X) 
 
Add this to an evergreen note [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=N69U7U5X) 
  
 <mark class="hltr-green">"Their economic value is substantial, and demand continues to grow globally, with China ranking as the top producer [2]."</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=K785GIFM) 
 
Tie this back to VN [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=K785GIFM) 
  
 <mark class="hltr-green">"Without timely harvesting, they can rapidly spoil, leading to reduced quality and financial  losses [3]."</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=GZHN2RH2) 
  
 <mark class="hltr-orange">"However, the limited memory and computing capabilities of edge devices present challenges for deploying such algorithms efficiently [4]."</mark> [Page 8469](zotero://open-pdf/library/items/VCG6DD4W?page=8469&annotation=Z2FRTN4S) 
  
 <mark class="hltr-yellow">"Classical techniques primarily utilize the visual features of strawberriessuch as color, shape, and surface texture—for identification."</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=5K4MKRTH) 
  
 <mark class="hltr-orange">"While these traditional methods can perform well under controlled conditions, they often struggle in more challenging scenarios involving complex backgrounds, variable illumination, and overlapping fruit clusters."</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=JYSI2AN7) 
  
 <mark class="hltr-yellow">"mong these, Convolutional Neural Networks (CNNs) have demonstrated outstanding capabilities in learning rich feature representations [9],"</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=4CETFDTT) 
  
 <mark class="hltr-yellow">"Within the deep learning paradigm, object detection algorithms are typically categorized into two main classes: single-stage and two-stage models."</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=GUHHVIIV) 
  
 <mark class="hltr-green">"deployment on resource-constrained edge devices, single-stage detectors are often preferred due to their streamlined architecture, low latency, and reduced computational burden."</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=B255SGRL) 
  
 <mark class="hltr-yellow">"Ji et al. [10] designed an apple detection model based on YOLOX, which achieved 26.3 frames per second (FPS) after TensorRT optimization on the Jetson Nano."</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=XWQ3XP6K) 
  
 <mark class="hltr-yellow">"Yang et al. [11] proposed a YOLOv5-based method for waxberry detection, successfully deploying it on a 2 GB Jetson Nano device with an FPS gain of 5.03 over the original YOLOv5."</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=6UU2XUVD) 
  
 <mark class="hltr-yellow">"un et al. [12] introduced a compact YOLOv5based passion fruit detection algorithm that achieved a realtime speed of 11.25 FPS and had a lightweight model size  of only 7.14 MB."</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=MKTEMQ9G) 
  
 <mark class="hltr-orange">"Firstly, in real-world agricultural scenes, strawberries are frequently occluded or surrounded by complex backgrounds, often resulting in missed or incorrect detections."</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=774B747Z) 
  
 <mark class="hltr-orange">"heavy occlusion can obscure vital features, impairing the model's ability to localize fruits accurately."</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=JVF8R2TJ) 
  
 <mark class="hltr-orange">"many existing models are computationally expensive and parameter-heavy, making them unsuitable for high-speed edge-based processing"</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=A7AWPYII) 
  
 <mark class="hltr-purple">"Datasets preparation"</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=URPJ628G) 
  
 <mark class="hltr-purple">"Acquisition of datasets"</mark> [Page 8470](zotero://open-pdf/library/items/VCG6DD4W?page=8470&annotation=3MP8SK9N) 
  
 <mark class="hltr-purple">"Augmentation of datasets"</mark> [Page 8472](zotero://open-pdf/library/items/VCG6DD4W?page=8472&annotation=QZQC7BGN) 
  
 <mark class="hltr-purple">"Methodologies"</mark> [Page 8473](zotero://open-pdf/library/items/VCG6DD4W?page=8473&annotation=98DWSYCU) 
  
 <mark class="hltr-purple">"Overview of YOLO11"</mark> [Page 8473](zotero://open-pdf/library/items/VCG6DD4W?page=8473&annotation=NF9Z5MGB) 
  
 <mark class="hltr-purple">"Improved strategy of YOLO11 model"</mark> [Page 8474](zotero://open-pdf/library/items/VCG6DD4W?page=8474&annotation=S4YW8TN2) 
  
 <mark class="hltr-purple">"Lightweight compact module based on PConv operator"</mark> [Page 8474](zotero://open-pdf/library/items/VCG6DD4W?page=8474&annotation=3XPZFA74) 
  
 <mark class="hltr-purple">"ELA(efficient local attention)"</mark> [Page 8476](zotero://open-pdf/library/items/VCG6DD4W?page=8476&annotation=V6EHEVNA) 
  
 <mark class="hltr-purple">"Localization‐based asymptotic feature pyramid network"</mark> [Page 8477](zotero://open-pdf/library/items/VCG6DD4W?page=8477&annotation=XUCG6MNA) 
  
 <mark class="hltr-purple">"Feature localization"</mark> [Page 8478](zotero://open-pdf/library/items/VCG6DD4W?page=8478&annotation=5KMU8GIN) 
  
 <mark class="hltr-purple">"Feature progressive fusion"</mark> [Page 8478](zotero://open-pdf/library/items/VCG6DD4W?page=8478&annotation=84JSPA5D) 
  
 <mark class="hltr-purple">"Focaler‐PIoU loss function"</mark> [Page 8479](zotero://open-pdf/library/items/VCG6DD4W?page=8479&annotation=B748CQE4) 
  
 <mark class="hltr-purple">"PIoU"</mark> [Page 8479](zotero://open-pdf/library/items/VCG6DD4W?page=8479&annotation=D8MBNRGW) 
  
 <mark class="hltr-purple">"Focaler‐IoU"</mark> [Page 8480](zotero://open-pdf/library/items/VCG6DD4W?page=8480&annotation=96DCNRN4) 
  
 <mark class="hltr-purple">"Synergistic loss"</mark> [Page 8481](zotero://open-pdf/library/items/VCG6DD4W?page=8481&annotation=A9TSF7UW) 
  
 <mark class="hltr-purple">"Results and discussion"</mark> [Page 8481](zotero://open-pdf/library/items/VCG6DD4W?page=8481&annotation=X552AV3P) 
  
 <mark class="hltr-purple">"Experiment setup"</mark> [Page 8481](zotero://open-pdf/library/items/VCG6DD4W?page=8481&annotation=K88EMKAS) 
  
 <mark class="hltr-purple">"Evaluation metrics"</mark> [Page 8482](zotero://open-pdf/library/items/VCG6DD4W?page=8482&annotation=HVGZII3C) 
  
 <mark class="hltr-purple">"Comparisons of different datasets"</mark> [Page 8483](zotero://open-pdf/library/items/VCG6DD4W?page=8483&annotation=CSC4JZU9) 
  
 <mark class="hltr-purple">"Comparison of different feature fusion structures"</mark> [Page 8483](zotero://open-pdf/library/items/VCG6DD4W?page=8483&annotation=9ZWZPMFG) 
  
 <mark class="hltr-purple">"Ablation study"</mark> [Page 8484](zotero://open-pdf/library/items/VCG6DD4W?page=8484&annotation=TAEHF9DJ) 
  
 <mark class="hltr-purple">"IoU loss function"</mark> [Page 8484](zotero://open-pdf/library/items/VCG6DD4W?page=8484&annotation=G5RTHH76) 
  
 <mark class="hltr-purple">"Overall strategies"</mark> [Page 8485](zotero://open-pdf/library/items/VCG6DD4W?page=8485&annotation=QNJIFUQC) 
  
 <mark class="hltr-purple">"Comparisons with state‐of‐the‐art models  To comprehensively evaluate the performance of"</mark> [Page 8486](zotero://open-pdf/library/items/VCG6DD4W?page=8486&annotation=UZD6WJL8) 
  
 <mark class="hltr-purple">"Tests on the edge computing platform"</mark> [Page 8488](zotero://open-pdf/library/items/VCG6DD4W?page=8488&annotation=PG25K883) 
  
 <mark class="hltr-purple">"Conclusion"</mark> [Page 8489](zotero://open-pdf/library/items/VCG6DD4W?page=8489&annotation=9VQY9ALL) 
  
 <mark class="hltr-orange">"the three-stage classification of ripeness adopted in this study simplifies the naturally continuous maturation process of strawberries, which may lead to misclassification near stage boundaries."</mark> [Page 8489](zotero://open-pdf/library/items/VCG6DD4W?page=8489&annotation=5M4LDP34) 
 
Create more rigorous classifications for stages of development of strawberry [Page 8489](zotero://open-pdf/library/items/VCG6DD4W?page=8489&annotation=5M4LDP34) 
  
 <mark class="hltr-orange">"its generalization may be limited under extreme agricultural conditions, such as heavy rain, dense fog, strong backlighting, or non-standard cultivation environments."</mark> [Page 8489](zotero://open-pdf/library/items/VCG6DD4W?page=8489&annotation=5QBP53R7) 
  
 <mark class="hltr-yellow">"developing a more fine-grained and continuous ripeness classification system that better reflects the full strawberry growth cycle"</mark> [Page 8489](zotero://open-pdf/library/items/VCG6DD4W?page=8489&annotation=NSM8F44X) 
  
 <mark class="hltr-yellow">"expanding the dataset to include samples from a broader range of environmental conditions, strawberry cultivars"</mark> [Page 8489](zotero://open-pdf/library/items/VCG6DD4W?page=8489&annotation=QGGH5MM6) 
  
