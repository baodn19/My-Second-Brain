---
title: "[[SP-RTSD - A Lightweight Real-Time Strawberry Detection on Edge Devices for Onboard Robotic Harvesting]]"
year: 2025 
authors: Yujie Chen, Aijing Shu, Zhanhao Liu, Yang Chen, Won Suk Lee, Yanchao Zhang
categories:
  - "[[Research References]]"
tags: 
- lightweight 
- edge-devices 
- real-time-detection 
- RTSD 
- SP-RTSD 
---

Zotero PDF Link: [[Zotero Attachments/Chen et al. - 2025 - SP-RTSD A Lightweight Real-Time Strawberry Detection on Edge Devices for Onboard Robotic Harvesting.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"ABSTRACT"</mark> [Page 3361](zotero://open-pdf/library/items/MJNYGGBZ?page=3361&annotation=YGTUWW2N) 
  
 <mark class="hltr-yellow">"in combination with RTSD, Superb Real‐time Strawberry Detection (SP‐RTSD),"</mark> [Page 3361](zotero://open-pdf/library/items/MJNYGGBZ?page=3361&annotation=QMBKKACD) 
  
 <mark class="hltr-yellow">"the C2f‐Faster module performs channel‐wise feature screening to enhance feature extraction efficiency while reducing model parameters"</mark> [Page 3361](zotero://open-pdf/library/items/MJNYGGBZ?page=3361&annotation=HZEGNHAQ) 
  
 <mark class="hltr-yellow">"a lightweight recognition head with a parameter sharing mechanism is proposed specially for the edge devices."</mark> [Page 3361](zotero://open-pdf/library/items/MJNYGGBZ?page=3361&annotation=7N26BMH2) 
  
 <mark class="hltr-orange">"In contrast to typical lightweight strategies, which often boost inference speed at the cost of accuracy"</mark> [Page 3361](zotero://open-pdf/library/items/MJNYGGBZ?page=3361&annotation=FQTB42JC) 
  
 <mark class="hltr-yellow">"SP‐RTSD achieves exceptional accuracy with a mean average precision (mAP) of 91.7%, slightly outperforming the original baseline model (90.7%)."</mark> [Page 3361](zotero://open-pdf/library/items/MJNYGGBZ?page=3361&annotation=Q6P94D2H) 
  
 <mark class="hltr-purple">"1 | Introduction"</mark> [Page 3361](zotero://open-pdf/library/items/MJNYGGBZ?page=3361&annotation=34JY78QH) 
  
 <mark class="hltr-green">"Traditional methods for target detection often rely on manually designed feature extraction and classifiers, involving the traversal of image data sets, feature extraction, and training classifiers to identify target images. Anraeni et al. (2021)."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=8EQEFKS6) 
  
 <mark class="hltr-yellow">"RGB feature extraction and the k‐Nearest Neighbors Algorithm (k‐NN) were employed to recognize strawberry fruit ripening. Lin et al. (2020),"</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=HZMEL9NH) 
  
 <mark class="hltr-yellow">"Rizon et al (Rizon et al. 2015) introduced a mango fruit detection method based on Hough transform, specifically designed to detect partially occluded and overlapped mango fruits by extracting texture features."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=S2NQGQMS) 
  
 <mark class="hltr-orange">"they often encounter challenges, such as poor robustness, high computational complexity, and diminished accuracy in practical applications."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=QEXQUNSS) 
  
 <mark class="hltr-yellow">"Bai et al. (2024) introduced the Swin Transformer detection head onto the YOLOv7 framework, enhancing the model's spatial interaction capabilities and feature extraction in scenes with similar colors and overlapping or obscured elements."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=HHTICZWW) 
  
 <mark class="hltr-yellow">"Li et al. (2024) proposed the YOLOv7‐Litchi method, which excels in detecting densely distributed lychee fruits that often occlude each other in complex backgrounds."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=E9VC3MPH) 
  
 <mark class="hltr-yellow">"Wang and He (2021). innovatively developed a channel‐pruned YOLOV5s model using transfer learning for rapid apple fruit detection before thinning."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=VDPR9KU5) 
  
 <mark class="hltr-yellow">"Pang and Chen (2023) introduced the MS‐YOLOv5 model, incorporating depth hybrid deformable convolution, a dual synergetic attention mechanism, and swift fusion of cross‐scale weights."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=IDNYIXKI) 
  
 <mark class="hltr-yellow">"Zhang  et al. (2022) proposed RTSD algorithm based on YOLOv4‐tiny. Through the reduction of CBL modules and convolutional layers in the CSPNet backbone,"</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=65NQVZ8Y) 
  
 <mark class="hltr-orange">"this approach comes with a slight sacrifice in accuracy, achieving a final accuracy of 82.25%, falling short of the practical detection accuracy requirements."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=VCUGLASG) 
  
 <mark class="hltr-yellow">"Zhou et al. (2023) designed a lightweight backbone utilizing the VGG architecture, resulting in a remarkable 76.35% reduction in parameters and a 38.75% reduction in inference time compared to the original model."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=DWK43ICN) 
  
 <mark class="hltr-orange">"the actual inference time when deployed to edge devices reached 926 ms, revealing a considerable gap from meeting the real‐time detection application requirements at edge devices."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=AIHTXU5V) 
  
 <mark class="hltr-yellow">"We investigate the reasons behind the failure of certain lightweighting strategies during real‐world deployment on edge devices, offering valuable insights that can guide future efforts in lightweight algorithm design for embedded systems."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=5IJSACDH) 
  
 <mark class="hltr-yellow">"We propose the C2f‐Faster module, which effectively extracts spatial features and channel information, significantly improving the accuracy of strawberry identification, particularly in complex environments with occlusion and shadows."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=JWLJ3J9H) 
  
 <mark class="hltr-yellow">"We develop the Lw‐Detect, a lightweight detection head with a parameter‐sharing mechanism, which substantially boosts the strawberry detection rate while maintaining high accuracy levels."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=BGN2BDYZ) 
  
 <mark class="hltr-yellow">"The SP‐RTSD model successfully balances both accuracy and inference speed, addressing the critical challenge of optimizing these factors for deployment on edge devices."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=7CXUNVPG) 
  
 <mark class="hltr-yellow">"Through a series of ablation studies, comparative model evaluations, data set validation experiments, and robotic simulation trials, we demonstrate the superiority and robustness of the SP‐RTSD model, confirming its suitability for real‐world applications in strawberry‐picking robots."</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=UJ7BBQCQ) 
  
 <mark class="hltr-purple">"2 | Materials and Methods"</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=RSU694SB) 
  
 <mark class="hltr-purple">"2.1 | System Setup"</mark> [Page 3362](zotero://open-pdf/library/items/MJNYGGBZ?page=3362&annotation=EKUATNS5) 
  
 <mark class="hltr-purple">"2.2 | Image Acquisition and Processing"</mark> [Page 3363](zotero://open-pdf/library/items/MJNYGGBZ?page=3363&annotation=D93U56PG) 
  
 <mark class="hltr-purple">"2.3 | Baseline Model"</mark> [Page 3363](zotero://open-pdf/library/items/MJNYGGBZ?page=3363&annotation=LZ7LMFU2) 
  
 <mark class="hltr-purple">"2.4 | Lightweighting Improvement Experiment"</mark> [Page 3365](zotero://open-pdf/library/items/MJNYGGBZ?page=3365&annotation=LL9Y9ZA2) 
  
 <mark class="hltr-purple">"2.4.1 | LAWDS Module"</mark> [Page 3365](zotero://open-pdf/library/items/MJNYGGBZ?page=3365&annotation=7JVKCD6R) 
  
 <mark class="hltr-purple">"2.4.2 | AIFI Module"</mark> [Page 3366](zotero://open-pdf/library/items/MJNYGGBZ?page=3366&annotation=5XCP6LZ9) 
  
 <mark class="hltr-purple">"2.5 | SP‐RTSD Network"</mark> [Page 3366](zotero://open-pdf/library/items/MJNYGGBZ?page=3366&annotation=Q633KAKT) 
  
 <mark class="hltr-purple">"2.5.1 | C2f‐Faster Module"</mark> [Page 3366](zotero://open-pdf/library/items/MJNYGGBZ?page=3366&annotation=DTDI2543) 
  
 <mark class="hltr-purple">"2.5.2 | Lw‐Detect Module"</mark> [Page 3368](zotero://open-pdf/library/items/MJNYGGBZ?page=3368&annotation=M8GXWULF) 
  
 <mark class="hltr-purple">"2.6 | Robotic Arm Gripping Simulation Experiment"</mark> [Page 3368](zotero://open-pdf/library/items/MJNYGGBZ?page=3368&annotation=BH4YHPIF) 
  
 <mark class="hltr-purple">"2.7 | Evaluation Criteria"</mark> [Page 3369](zotero://open-pdf/library/items/MJNYGGBZ?page=3369&annotation=I2DCHNYI) 
  
 <mark class="hltr-purple">"3 | Experimental Results and Analysis"</mark> [Page 3369](zotero://open-pdf/library/items/MJNYGGBZ?page=3369&annotation=MCTW6TB3) 
  
 <mark class="hltr-purple">"3.1 | Experimental Platform and Parameter Configuration"</mark> [Page 3369](zotero://open-pdf/library/items/MJNYGGBZ?page=3369&annotation=XDJC74KA) 
  
 <mark class="hltr-purple">"3.2 | Results and Discussion of Lightweighting Improvement Experiment"</mark> [Page 3370](zotero://open-pdf/library/items/MJNYGGBZ?page=3370&annotation=G7QLBZFZ) 
  
 <mark class="hltr-purple">"3.3 | Comparison With State‐of‐The‐Art Models"</mark> [Page 3372](zotero://open-pdf/library/items/MJNYGGBZ?page=3372&annotation=37NRPLDX) 
  
 <mark class="hltr-purple">"3.4 | Network Improvement Ablation Experiments"</mark> [Page 3372](zotero://open-pdf/library/items/MJNYGGBZ?page=3372&annotation=EQF5EAF9) 
  
 <mark class="hltr-purple">"3.5 | Evaluation of Model Performance"</mark> [Page 3374](zotero://open-pdf/library/items/MJNYGGBZ?page=3374&annotation=GWT7YKSE) 
  
 <mark class="hltr-purple">"3.5.1 | Comparison Experiments With Other Advanced Lightweighting Models"</mark> [Page 3374](zotero://open-pdf/library/items/MJNYGGBZ?page=3374&annotation=48BXMTTL) 
  
 <mark class="hltr-purple">"3.5.2 | Robustness Test Experiment With Different Strawberry Data"</mark> [Page 3375](zotero://open-pdf/library/items/MJNYGGBZ?page=3375&annotation=PDA4Y5JE) 
  
 <mark class="hltr-purple">"3.6 | Experimental Resu"</mark> [Page 3377](zotero://open-pdf/library/items/MJNYGGBZ?page=3377&annotation=KN8BWMTN) 
  
 <mark class="hltr-purple">"4 | Discussion"</mark> [Page 3378](zotero://open-pdf/library/items/MJNYGGBZ?page=3378&annotation=X5TCXMUP) 
  
 <mark class="hltr-purple">"5 | Conclusion"</mark> [Page 3378](zotero://open-pdf/library/items/MJNYGGBZ?page=3378&annotation=RQ7SY6UD) 
  
 <mark class="hltr-orange">"We explored the effectiveness of common lightweight techniques on edge devices and discovered that when these methods conflict with the deployment strategies of edge devices, they may fail."</mark> [Page 3379](zotero://open-pdf/library/items/MJNYGGBZ?page=3379&annotation=C3T7MPV7) 
  
 <mark class="hltr-orange">"This explains why certain lightweight models perform well on PCs but show counterproductive results when implemented on edge devices."</mark> [Page 3379](zotero://open-pdf/library/items/MJNYGGBZ?page=3379&annotation=2UCPZYTG) 
  
 <mark class="hltr-orange">"While fruit detection is crucial to the picking process, key point detection is also critical for the successful operation of a picking robot."</mark> [Page 3379](zotero://open-pdf/library/items/MJNYGGBZ?page=3379&annotation=B8QGYQKU) 
  
