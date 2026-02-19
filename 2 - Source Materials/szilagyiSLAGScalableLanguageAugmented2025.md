---
title: "[[SLAG - Scalable Language-Augmented Gaussian Splatting]]"
year: 2025 
authors: Laszlo Szilagyi, Francis Engelmann, Jeannette Bohg
categories:
  - "[[Research References]]"
tags: 
- Computer-Science---Artificial-Intelligence 
- Computer-Science---Computer-Vision-and-Pattern-Recognition 
- Computer-Science---Robotics 
---

Zotero PDF Link: [[Zotero Attachments/Szilagyi et al. - 2025 - SLAG Scalable Language-Augmented Gaussian Splatting.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"Abstract"</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=A9AWE8LH) 
  
 <mark class="hltr-yellow">"integrates 2D visual-language model features into 3D scenes using SAM [1] and CLIP [2]."</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=JFJRUYKK) 
  
 <mark class="hltr-yellow">"SLAG eliminates the need for a loss function to compute perGaussian language embeddings. Instead, it derives embeddings from 3D Gaussian scene parameters via a normalized weighted average, enabling highly parallelized scene encoding."</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=6BA3PDBF) 
  
 <mark class="hltr-yellow">"introduce a vector database for efficient embedding storage and retrieval."</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=HWMH9A79) 
  
 <mark class="hltr-purple">"I. INTRODUCTION"</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=DAZWACJC) 
  
 <mark class="hltr-yellow">"R  ECENT progress in 3D scene representations [3], [5]–[9] enhances 3D reconstruction techniques such as NeRF [10] and Gaussian Splatting [11] by integrating language embeddings from 2D vision-language models like CLIP [2]."</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=5M67G8NK) 
  
 <mark class="hltr-yellow">"Unlike traditional 3D segmentation methods [12]–[14], these approaches typically reconstruct the scene using NeRF or Gaussian Splatting, extract language- aligned embeddings, and enable querying the scene based on natural language."</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=JY8J2R88) 
  
 <mark class="hltr-yellow">"robots performing open-vocabulary search over vast areas, enabling an LLM-based planner to query object locations beyond the line of sight."</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=F3KTJFDB) 
  
 <mark class="hltr-orange">"in time-sensitive scenarios, the drone’s survey data must be processed rapidly in the cloud (e.g., within 10 minutes)"</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=GPNIBDL8) 
  
 <mark class="hltr-orange">"encoding large-scale scenes is highly memory-intensive and may exceed the capacity of a single GPU"</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=6XDA4CVM) 
  
 <mark class="hltr-orange">"the encoded scene—or its relevant portions—must be compact enough for deployment on a robot while remaining efficient for real-time querying."</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=6L3YBXLA) 
  
 <mark class="hltr-red">"we introduce a highly scalable approach to language-embedded Gaussian splatting that enhances processing speed, alleviates memory constraints, and enables deployment in resource-limited environments."</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=PIUQKFC5) 
 
how is it scalable [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=PIUQKFC5) 
  
 <mark class="hltr-yellow">"SLAG eliminates the need for a loss function to compute per-Gaussian language embeddings. Instead, it leverages 3D Gaussian scene parameters, computing each embedding as a normalized weighted average."</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=77CNG7VI) 
  
 <mark class="hltr-yellow">"Our approach maps SAM [1]-masked CLIP [2] embeddings onto the 3D Gaussian splatting scene using a modified Gaussian splatting rasterizer."</mark> [Page 1](zotero://open-pdf/library/items/8G5MLH35?page=1&annotation=IAEYPHIM) 
  
 <mark class="hltr-yellow">"To enhance scalability and inference performance, we store semantic embeddings separately from the Gaussian splatting model."</mark> [Page 2](zotero://open-pdf/library/items/8G5MLH35?page=2&annotation=GVPFQ3SF) 
  
 <mark class="hltr-yellow">"further optimize embedding retrieval and improve usability for downstream tasks, we propose leveraging a vector database."</mark> [Page 2](zotero://open-pdf/library/items/8G5MLH35?page=2&annotation=GP9RCIYM) 
  
 <mark class="hltr-orange">"However, deploying the entire vector database on a robot may be impractical due to its size and the associated query processing overhead."</mark> [Page 2](zotero://open-pdf/library/items/8G5MLH35?page=2&annotation=HNW5V4MV) 
  
 <mark class="hltr-yellow">"we introduce a partitioning mechanism that reduces both storage requirements and query latency for resource-constrained edge devices."</mark> [Page 2](zotero://open-pdf/library/items/8G5MLH35?page=2&annotation=56MHZLJY) 
  
 <mark class="hltr-yellow">"highly parallelizable Gaussian scene language embedding method that enables efficient multiGPU implementation, scaling up to process individual input images in parallel."</mark> [Page 2](zotero://open-pdf/library/items/8G5MLH35?page=2&annotation=LF6Z8RF6) 
  
 <mark class="hltr-yellow">"decouple the language embeddings from the Gaussian splatting model, enabling storage and processing the language embeddings outside the GPU to address memory bottlenecks."</mark> [Page 2](zotero://open-pdf/library/items/8G5MLH35?page=2&annotation=V6DLXP6V) 
  
 <mark class="hltr-yellow">"implement and benchmark a system with 16 GPUs."</mark> [Page 2](zotero://open-pdf/library/items/8G5MLH35?page=2&annotation=N57CWXY9) 
  
 <mark class="hltr-yellow">"propose the use of a vector database for language"</mark> [Page 2](zotero://open-pdf/library/items/8G5MLH35?page=2&annotation=GX2DRD3Y) 
  
 <mark class="hltr-purple">"II. RELATED WORK"</mark> [Page 2](zotero://open-pdf/library/items/8G5MLH35?page=2&annotation=LVUYF9QY) 
  
 <mark class="hltr-purple">"III. METHOD"</mark> [Page 3](zotero://open-pdf/library/items/8G5MLH35?page=3&annotation=JKDYCKQQ) 
  
 <mark class="hltr-yellow">"The Scene Reconstruction, Semantic Embedding, and Vector Database and Partitioning stages collectively form the scene encoding phase of the algorithm. This phase is executed once in the cloud for a given Scene Capture dataset."</mark> [Page 3](zotero://open-pdf/library/items/8G5MLH35?page=3&annotation=CKT79P8H) 
  
 <mark class="hltr-orange">"For larger scenes that exceed the memory capacity of a single GPU, aggregation must be performed iteratively over subsets of the EGAUSSIAN tensor and wk,p weights."</mark> [Page 5](zotero://open-pdf/library/items/8G5MLH35?page=5&annotation=VXG95B8P) 
  
 <mark class="hltr-purple">"IV. EXPERIMENTS"</mark> [Page 5](zotero://open-pdf/library/items/8G5MLH35?page=5&annotation=ML9LUNBL) 
  
 <mark class="hltr-orange">"Notably, the SAM execution time dominates the overall runtime. As detailed in the Parameter Analysis section IV, switching from the 16 × 16 to the 32 × 32 SAM grid sampling configuration, which offers slightly better performance, comes at the cost of more than double the SAM execution time."</mark> [Page 5](zotero://open-pdf/library/items/8G5MLH35?page=5&annotation=X6CSW4RF) 
  
 <mark class="hltr-orange">"Note that the multi-GPU execution speed is determined by the GPU batch with the longest execution time. As shown in Fig. 6, execution times vary significantly between batches. This variation arises because the number of SAM masks varies between training images, directly impacting the number of processing operations."</mark> [Page 5](zotero://open-pdf/library/items/8G5MLH35?page=5&annotation=RZ5HSNPY) 
  
 <mark class="hltr-orange">"It takes only 1 second, even if executed on a single GPU. The extent of parallelization is limited by the number of GPUs."</mark> [Page 6](zotero://open-pdf/library/items/8G5MLH35?page=6&annotation=7FWVUP86) 
  
 <mark class="hltr-purple">"V. CONCLUSION"</mark> [Page 8](zotero://open-pdf/library/items/8G5MLH35?page=8&annotation=NA7KFC9Z) 
  
