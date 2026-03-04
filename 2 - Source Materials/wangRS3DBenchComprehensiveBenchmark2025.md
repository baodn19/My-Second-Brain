---
title: "[[RS3DBench - A Comprehensive Benchmark for 3D Spatial Perception in Remote Sensing]]"
year: 2025 
authors: Jiayu Wang, Ruizhi Wang, Jie Song, Haofei Zhang, Mingli Song, Zunlei Feng, Li Sun
categories:
  - "[[Research References]]"
tags: 
- Computer-Science---Computer-Vision-and-Pattern-Recognition 
---

Zotero PDF Link: [[Zotero Attachments/Wang et al. - 2025 - RS3DBench A Comprehensive Benchmark for 3D Spatial Perception in Remote Sensing.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"Abstract"</mark> [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=PH4WLK7A) 
  
 <mark class="hltr-orange">"While several datasets have been proposed within the realm of remote sensing, many existing collections either lack comprehensive depth information or fail to establish precise alignment between depth data and remote sensing images."</mark> [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=F9CFD8FH) 
  
 <mark class="hltr-yellow">"This dataset encompasses 54,951 pairs of remote sensing images and pixel-level aligned depth maps, accompanied by corresponding textual descriptions, spanning a broad array of geographical contexts."</mark> [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=MQVGMRN6) 
  
 <mark class="hltr-yellow">"we introduce a remotely sensed depth estimation model derived from stable diffusion, harnessing its multimodal fusion capabilities, thereby delivering state-of-the-art performance on our dataset."</mark> [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=J6RJBHPX) 
  
 <mark class="hltr-purple">"1 Introduction"</mark> [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=M5VUK3HA) 
  
 <mark class="hltr-green">"Remote sensing systems [1] have emerged as pivotal tools for large-scale geospatial intelligence, leveraging multi-spectral satellite imagery to decode the Earth’s surface with centimeter-to-meter scale resolution."</mark> [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=TWJSVCGY) 
  
 <mark class="hltr-green">"crop phenotyping via hyperspectral imaging [4]"</mark> [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=DUH7RXBF) 
 
relate to my work in crop phenotyping [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=DUH7RXBF) 
  
 <mark class="hltr-yellow">"remote sensing data holds transformative potential for visual-language navigation (VLN), with indoor benchmarks such as R2R [6] and VLN-CE [7] demonstrating considerable success."</mark> [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=32U4MDRQ) 
 
Other benchmark to refer to [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=32U4MDRQ) 
  
 <mark class="hltr-orange">"expanding agent interaction environments from indoor to outdoor scenarios necessitates the comprehension of large-scale terrain morphology and complex multi-altitude spatial relationships, encountering a critical bottleneck: the absence of spatially anchored datasets capable of bridging aerial perspective reasoning with terrain-level semantics."</mark> [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=GT6ZXPCE) 
  
 <mark class="hltr-orange">"Height information, as the cornerstone of 3D geospatial reasoning, remains constrained by sensor physics: Airborne LiDAR delivers centimeter-level precision at operational costs exceeding hundreds of dollars/km2, whereas InSAR and PRISM stereo imaging necessitate meticulous flight"</mark> [Page 1](zotero://open-pdf/library/items/5QKJWDEE?page=1&annotation=4VD7CVIJ) 
  
 <mark class="hltr-orange">"planning and multi-sensor calibration [8]."</mark> [Page 2](zotero://open-pdf/library/items/5QKJWDEE?page=2&annotation=7TT7F9AZ) 
  
 <mark class="hltr-yellow">"3D visual perception models grounded in deep learning have precipitated a paradigmatic shift in the analysis of natural scene structures [9, 10, 11, 12, 13, 14, 15, 16], achieved through synergistic optimization of multimodal data fusion (encompassing RGB-D inputs, LiDAR point clouds, and multi-view imagery) and geometric prior encoding [17, 18, 19, 20, 21, 22]."</mark> [Page 2](zotero://open-pdf/library/items/5QKJWDEE?page=2&annotation=VFIRXR4E) 
  
 <mark class="hltr-orange">"(i) Data Distribution Disparity. The domain discrepancy between proximal sensing modalities (e.g., indoor RGB-D sensors, vehicular LiDAR) and satellite remote sensing systems originates from fundamental differences in imaging physics that manifest most acutely in scale-space representations [25, 26], particularly in scale representation. Critical ground objects (e.g., vehicles, minor infrastructure) span a mere 10∼20 pixels in sub-meter resolution images, rendering conventional convolutional kernel-based feature extractors inadequate for capturing salient geometric features [27]."</mark> [Page 2](zotero://open-pdf/library/items/5QKJWDEE?page=2&annotation=5A2WEK7G) 
  
 <mark class="hltr-orange">"(ii) Absence of Depth Information: Current remote sensing datasets exhibit significant limitations in 3D perception tasks due to: (1) lack of depth annotations, and (2) misalignment of depth and RGB data."</mark> [Page 2](zotero://open-pdf/library/items/5QKJWDEE?page=2&annotation=6DSKK3UF) 
  
 <mark class="hltr-orange">"For the former, predominant remote sensing datasets furnish only 2D bounding boxes and categorical labels [28, 29], devoid of elevation or surface geometry descriptors. This constraint compels models to resort to weakly supervised approaches (e.g. [30], inferring height from shadow length)."</mark> [Page 2](zotero://open-pdf/library/items/5QKJWDEE?page=2&annotation=3LH98JNL) 
  
 <mark class="hltr-orange">"even the limited datasets containing depth information frequently lack corresponding RGB imagery with pixel-level registration, further exacerbating the challenge of accurate 3D reconstruction."</mark> [Page 2](zotero://open-pdf/library/items/5QKJWDEE?page=2&annotation=XT9XE5VF) 
  
 <mark class="hltr-yellow">"our research introduces RS3DBench, a new universal benchmark that includes 54,951 pairs of pixel-aligned remote sensing images, depth information, and text descriptions, covering multiple countries across four continents, as well as six major terrain types for 3D visual understanding of remote sensing images."</mark> [Page 2](zotero://open-pdf/library/items/5QKJWDEE?page=2&annotation=J8YFH36H) 
  
 <mark class="hltr-yellow">"We propose an innovative semi-automated 3D vision data acquisition pipeline comprising four critical stages: RGB and depth data capture, depth alignment, GLM-v4 inference, and human validation. This framework enables efficient compilation of extensive, high-quality datasets enriched with depth information."</mark> [Page 3](zotero://open-pdf/library/items/5QKJWDEE?page=3&annotation=SWXZRS4N) 
  
 <mark class="hltr-yellow">"We proposed a novel multimodal fusion method that integrates geographic semantic information from remote sensing images into the diffusion process of a pretrained stable diffusion model for depth estimation in the form of text, achieving state-of-the-art performance on our dataset."</mark> [Page 3](zotero://open-pdf/library/items/5QKJWDEE?page=3&annotation=84BXL7JS) 
  
 <mark class="hltr-yellow">"We built a rigorous benchmarking framework based on the RS3DBench dataset, developed a comprehensive evaluation protocol, and evaluated the performance of several state-of-the-art depth estimation models."</mark> [Page 3](zotero://open-pdf/library/items/5QKJWDEE?page=3&annotation=D55DTLCL) 
  
 <mark class="hltr-yellow">"Our study establishes that geosemantic text embeddings can effectively enhance remote sensing depth estimation through diffusion frameworks, with rigorous validation conducted on the RS3DBench benchmark."</mark> [Page 3](zotero://open-pdf/library/items/5QKJWDEE?page=3&annotation=39P624S8) 
  
 <mark class="hltr-purple">"2 Related Work"</mark> [Page 3](zotero://open-pdf/library/items/5QKJWDEE?page=3&annotation=I9IKUT7F) 
  
 <mark class="hltr-purple">"3 Proposed RS3DBench Dataset"</mark> [Page 4](zotero://open-pdf/library/items/5QKJWDEE?page=4&annotation=Z93ZLVCZ) 
  
 <mark class="hltr-purple">"3.1 Pipeline of Constructing the RS3DBench Dataset"</mark> [Page 4](zotero://open-pdf/library/items/5QKJWDEE?page=4&annotation=GUUJDGNG) 
  
 <mark class="hltr-purple">"3.2 Dataset statistics and analysis"</mark> [Page 6](zotero://open-pdf/library/items/5QKJWDEE?page=6&annotation=6UXAZJVU) 
  
 <mark class="hltr-purple">"4 Marigold-RS"</mark> [Page 6](zotero://open-pdf/library/items/5QKJWDEE?page=6&annotation=SUUNDBF6) 
  
 <mark class="hltr-purple">"4.1 Generative Formulation"</mark> [Page 6](zotero://open-pdf/library/items/5QKJWDEE?page=6&annotation=LLVZ624I) 
  
 <mark class="hltr-purple">"4.2 Depth estimation framework with text guidance"</mark> [Page 7](zotero://open-pdf/library/items/5QKJWDEE?page=7&annotation=UMQZ6WP8) 
  
 <mark class="hltr-purple">"5 Benchmarks"</mark> [Page 7](zotero://open-pdf/library/items/5QKJWDEE?page=7&annotation=NNPCUQIH) 
  
 <mark class="hltr-purple">"5.1 Cross-Domain Adaptability of Traditional Depth Models in Remote Sensing"</mark> [Page 7](zotero://open-pdf/library/items/5QKJWDEE?page=7&annotation=L6TWHZBH) 
  
 <mark class="hltr-purple">"5.2 Efficiency Benchmarking"</mark> [Page 8](zotero://open-pdf/library/items/5QKJWDEE?page=8&annotation=6NW9HAQK) 
  
 <mark class="hltr-purple">"5.3 Model Generalization Across Terrain Variations"</mark> [Page 8](zotero://open-pdf/library/items/5QKJWDEE?page=8&annotation=JTDKN4FU) 
  
 <mark class="hltr-purple">"5.4 Text-Driven Depth Estimation"</mark> [Page 9](zotero://open-pdf/library/items/5QKJWDEE?page=9&annotation=BA6RV2KB) 
  
 <mark class="hltr-purple">"6 Conclusion"</mark> [Page 9](zotero://open-pdf/library/items/5QKJWDEE?page=9&annotation=KTREGB7V) 
  
 <mark class="hltr-orange">"The current method does not use time series information, so the dataset lacks continuous observations."</mark> [Page 9](zotero://open-pdf/library/items/5QKJWDEE?page=9&annotation=U5H2GWAP) 
 
Research gap [Page 9](zotero://open-pdf/library/items/5QKJWDEE?page=9&annotation=U5H2GWAP) 
  
 <mark class="hltr-yellow">"spatiotemporal joint modeling by introducing time series remote sensing data and supporting longitudinal research on land surface change monitoring, and promote the development of 3D geospatial intelligence."</mark> [Page 9](zotero://open-pdf/library/items/5QKJWDEE?page=9&annotation=PB2XRNJI) 
  
 <mark class="hltr-purple">"A Appendix"</mark> [Page 14](zotero://open-pdf/library/items/5QKJWDEE?page=14&annotation=3ETR845Q) 
  
 <mark class="hltr-purple">"A.1 Details of Dataset"</mark> [Page 14](zotero://open-pdf/library/items/5QKJWDEE?page=14&annotation=XDLGHGMU) 
  
 <mark class="hltr-purple">"A.1.1 Depth data"</mark> [Page 14](zotero://open-pdf/library/items/5QKJWDEE?page=14&annotation=ZHIA7GUY) 
  
 <mark class="hltr-purple">"A.1.2 Data Availability"</mark> [Page 15](zotero://open-pdf/library/items/5QKJWDEE?page=15&annotation=R28JI9HZ) 
  
 <mark class="hltr-purple">"A.1.3 Text annotations"</mark> [Page 15](zotero://open-pdf/library/items/5QKJWDEE?page=15&annotation=CBVVSTR9) 
  
 <mark class="hltr-purple">"A.1.4 Linear stretching"</mark> [Page 15](zotero://open-pdf/library/items/5QKJWDEE?page=15&annotation=DKGATCYE) 
  
 <mark class="hltr-purple">"A.2 Details of Experiments"</mark> [Page 16](zotero://open-pdf/library/items/5QKJWDEE?page=16&annotation=V7EJD8LX) 
  
 <mark class="hltr-purple">"A.2.1 Evaluation protocol"</mark> [Page 16](zotero://open-pdf/library/items/5QKJWDEE?page=16&annotation=R2CWYLT8) 
  
 <mark class="hltr-purple">"A.2.2 Test Datasets"</mark> [Page 17](zotero://open-pdf/library/items/5QKJWDEE?page=17&annotation=KAXQ959U) 
  
 <mark class="hltr-purple">"A.2.3 Implementation Details"</mark> [Page 17](zotero://open-pdf/library/items/5QKJWDEE?page=17&annotation=PNKV7WQU) 
  
 <mark class="hltr-purple">"NeurIPS Paper Checklist"</mark> [Page 20](zotero://open-pdf/library/items/5QKJWDEE?page=20&annotation=I69VDT4L) 
  
 <mark class="hltr-purple">"1. Claims"</mark> [Page 20](zotero://open-pdf/library/items/5QKJWDEE?page=20&annotation=8J382UGS) 
  
 <mark class="hltr-purple">"2. Limitations"</mark> [Page 20](zotero://open-pdf/library/items/5QKJWDEE?page=20&annotation=QNA9DXPJ) 
  
 <mark class="hltr-purple">"3. Theory assumptions and proofs"</mark> [Page 20](zotero://open-pdf/library/items/5QKJWDEE?page=20&annotation=SHTTLDKG) 
  
 <mark class="hltr-purple">"4. Experimental result reproducibility"</mark> [Page 21](zotero://open-pdf/library/items/5QKJWDEE?page=21&annotation=C6D4HSNY) 
  
 <mark class="hltr-purple">"5. Open access to data and code"</mark> [Page 21](zotero://open-pdf/library/items/5QKJWDEE?page=21&annotation=CR6UWBXJ) 
  
 <mark class="hltr-purple">"6. Experimental setting/details"</mark> [Page 22](zotero://open-pdf/library/items/5QKJWDEE?page=22&annotation=EH8R5Q7P) 
  
 <mark class="hltr-purple">"7. Experiment statistical significance"</mark> [Page 22](zotero://open-pdf/library/items/5QKJWDEE?page=22&annotation=CJLH33PT) 
  
 <mark class="hltr-purple">"8. Experiments compute resources"</mark> [Page 23](zotero://open-pdf/library/items/5QKJWDEE?page=23&annotation=X5AA9JG4) 
  
 <mark class="hltr-purple">"9. Code of ethics"</mark> [Page 23](zotero://open-pdf/library/items/5QKJWDEE?page=23&annotation=SAIMSEIJ) 
  
 <mark class="hltr-purple">"10. Broader impacts"</mark> [Page 23](zotero://open-pdf/library/items/5QKJWDEE?page=23&annotation=JYHGLB6T) 
  
 <mark class="hltr-purple">"11. Safeguards"</mark> [Page 24](zotero://open-pdf/library/items/5QKJWDEE?page=24&annotation=6AF4PDLZ) 
  
 <mark class="hltr-purple">"12. Licenses for existing assets"</mark> [Page 24](zotero://open-pdf/library/items/5QKJWDEE?page=24&annotation=KPL6MXXY) 
  
 <mark class="hltr-purple">"13. New assets"</mark> [Page 25](zotero://open-pdf/library/items/5QKJWDEE?page=25&annotation=TXQ2L7JZ) 
  
 <mark class="hltr-purple">"14. Crowdsourcing and research with human subjects"</mark> [Page 25](zotero://open-pdf/library/items/5QKJWDEE?page=25&annotation=P6H375HF) 
  
 <mark class="hltr-purple">"15. Institutional review board (IRB) approvals or equivalent for research with human subjects"</mark> [Page 25](zotero://open-pdf/library/items/5QKJWDEE?page=25&annotation=RVX5MAAM) 
  
 <mark class="hltr-purple">"16. Declaration of LLM usage"</mark> [Page 26](zotero://open-pdf/library/items/5QKJWDEE?page=26&annotation=BJV8LLHX) 
  
