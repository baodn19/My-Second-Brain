---
title: "[[World Action Models are Zero-shot Policies]]"
year: 2026
authors: Seonghyeon Ye, Yunhao Ge, Kaiyuan Zheng, Shenyuan Gao, Sihyun Yu, George Kurian, Suneel Indupuru, You Liang Tan, Chuning Zhu, Jiannan Xiang, Ayaan Malik, Kyungmin Lee, William Liang, Nadun Ranawaka, Jiasheng Gu, Yinzhen Xu, Guanzhi Wang, Fengyuan Hu, Avnish Narayan, Johan Bjorck, Jing Wang, Gwanghyun Kim, Dantong Niu, Ruijie Zheng, Yuqi Xie, Jimmy Wu, Qi Wang, Ryan Julian, Danfei Xu, Yilun Du, Yevgen Chebotar, Scott Reed, Jan Kautz, Yuke Zhu, Linxi "Jim" Fan, Joel Jang
categories:
  - "[[Research References]]"
tags:
  - Computer-Science---Computer-Vision-and-Pattern-Recognition
  - Computer-Science---Machine-Learning
  - Computer-Science---Robotics
modified: April 25th 2026, 10:40:47 pm
---

Zotero PDF Link: [[Zotero Attachments/Ye et al. - 2026 - World Action Models are Zero-shot Policies.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"Abstract"</mark> [Page 2](zotero://open-pdf/library/items/CQJWWM37?page=2&annotation=D5SF93VQ) 
  
 <mark class="hltr-purple">"1. Introduction"</mark> [Page 2](zotero://open-pdf/library/items/CQJWWM37?page=2&annotation=3E5MVRYI) 
  
 <mark class="hltr-orange">"their generalization to novel environments and, more critically, to new motions or skills remains limited"</mark> [Page 2](zotero://open-pdf/library/items/CQJWWM37?page=2&annotation=RZ7UFK9X) 
  
 <mark class="hltr-yellow">"This shifts action learning from dense state–action imitation to inverse dynamics—aligning motor commands with predicted visual futures."</mark> [Page 2](zotero://open-pdf/library/items/CQJWWM37?page=2&annotation=Y5NPUVH3) 
  
 <mark class="hltr-yellow">"(1) effective learning from robot data that are heterogeneous trajectories collected during the execution of useful behaviors"</mark> [Page 2](zotero://open-pdf/library/items/CQJWWM37?page=2&annotation=L944GGIT) 
  
 <mark class="hltr-yellow">"(2) zero-shot generalization to new tasks in new environments"</mark> [Page 2](zotero://open-pdf/library/items/CQJWWM37?page=2&annotation=SR5V64XM) 
  
 <mark class="hltr-yellow">"(3) efficient cross-embodiment transfer."</mark> [Page 2](zotero://open-pdf/library/items/CQJWWM37?page=2&annotation=Q7D2W4NA) 
  
 <mark class="hltr-yellow">"First, DreamZero unlocks new generalization capabilities beyond traditional VLAs and previous WAMs—across environments, across tasks, and across embodiments"</mark> [Page 2](zotero://open-pdf/library/items/CQJWWM37?page=2&annotation=G3GUHL69) 
  
 <mark class="hltr-yellow">"Second, DreamZero demonstrates that generalist policies can be learned effectively from diverse, heterogeneous data, breaking away from the conventional wisdom that generalist robot policies require multiple repeated"</mark> [Page 2](zotero://open-pdf/library/items/CQJWWM37?page=2&annotation=KATKHGE6) 
  
 <mark class="hltr-yellow">"demonstrations per task."</mark> [Page 3](zotero://open-pdf/library/items/CQJWWM37?page=3&annotation=ICLQD9BX) 
  
 <mark class="hltr-yellow">"Lastly, we demonstrate two forms of cross-embodiment transfer. First, video-only demonstrations from another robot (YAM) or humans yield a relative improvement of over 42% on unseen task performance for the target robot (AgiBot G1) with just 10–20 minutes of data. Second, and more surprisingly, we show that DreamZero enables few-shot embodiment adaptation: a model pretrained on AgiBot G1 adapts to an entirely new robot (YAM) with only 30 minutes of play data, retaining zero-shot generalization."</mark> [Page 3](zotero://open-pdf/library/items/CQJWWM37?page=3&annotation=U7WB4LWI) 
  
 <mark class="hltr-yellow">"Our architectural analysis reveals that larger pretrained video diffusion models produce higher-quality video predictions, which directly translates to superior downstream action execution—indicating that policy performance is fundamentally tied to video generation quality."</mark> [Page 3](zotero://open-pdf/library/items/CQJWWM37?page=3&annotation=69DGYESA) 
  
 <mark class="hltr-orange">"address the computational overhead inherent to video diffusion models"</mark> [Page 3](zotero://open-pdf/library/items/CQJWWM37?page=3&annotation=G8ABXX5D) 
  
 <mark class="hltr-yellow">"(1) algorithmic improvements, including decoupled video and action denoising schedules (DreamZero-Flash)"</mark> [Page 3](zotero://open-pdf/library/items/CQJWWM37?page=3&annotation=X3UUVF48) 
  
 <mark class="hltr-yellow">"(2) system-level parallelism and caching strategies"</mark> [Page 3](zotero://open-pdf/library/items/CQJWWM37?page=3&annotation=CINQVAHA) 
  
 <mark class="hltr-yellow">"(3) low-level optimizations such as quantization, and CUDA kernel tuning"</mark> [Page 3](zotero://open-pdf/library/items/CQJWWM37?page=3&annotation=NIVBVK88) 
  
 <mark class="hltr-yellow">"these techniques achieve a 38× inference speedup without degrading performance, enabling DreamZero to generate action chunks at approximately 7Hz for smooth, real-time robotic control."</mark> [Page 3](zotero://open-pdf/library/items/CQJWWM37?page=3&annotation=VN8T4GAD) 
  
 <mark class="hltr-purple">"2. Related Work"</mark> [Page 4](zotero://open-pdf/library/items/CQJWWM37?page=4&annotation=GLETKR56) 
  
 <mark class="hltr-purple">"2.1. Vision Language Action Models"</mark> [Page 4](zotero://open-pdf/library/items/CQJWWM37?page=4&annotation=8QCIC7WY) 
  
 <mark class="hltr-purple">"2.2. Video Model-based Robot Policies"</mark> [Page 5](zotero://open-pdf/library/items/CQJWWM37?page=5&annotation=MTP32B7Z) 
  
 <mark class="hltr-purple">"3. DreamZero"</mark> [Page 6](zotero://open-pdf/library/items/CQJWWM37?page=6&annotation=GVQ8XL5Z) 
  
 <mark class="hltr-purple">"3.1. Model Architecture"</mark> [Page 6](zotero://open-pdf/library/items/CQJWWM37?page=6&annotation=FF5GTPVU) 
  
 <mark class="hltr-purple">"3.2. Real-time Execution of DreamZero"</mark> [Page 8](zotero://open-pdf/library/items/CQJWWM37?page=8&annotation=2ML9229Y) 
  
 <mark class="hltr-purple">"3.2.1. The Reactivity Gap"</mark> [Page 8](zotero://open-pdf/library/items/CQJWWM37?page=8&annotation=Y2JTQZMX) 
  
 <mark class="hltr-purple">"3.2.2. Asynchronous Closed-Loop Execution"</mark> [Page 8](zotero://open-pdf/library/items/CQJWWM37?page=8&annotation=PE7PXUIJ) 
  
 <mark class="hltr-purple">"3.2.3. System-level Optimizations"</mark> [Page 8](zotero://open-pdf/library/items/CQJWWM37?page=8&annotation=3N4BXEDH) 
  
 <mark class="hltr-purple">"3.2.4. Implementation-level Optimizations"</mark> [Page 8](zotero://open-pdf/library/items/CQJWWM37?page=8&annotation=H5EZ2TUH) 
  
 <mark class="hltr-purple">"3.2.5. Model-level Optimizations: DreamZero-Flash"</mark> [Page 9](zotero://open-pdf/library/items/CQJWWM37?page=9&annotation=F2FEHZIU) 
  
 <mark class="hltr-purple">"3.2.6. Summary"</mark> [Page 9](zotero://open-pdf/library/items/CQJWWM37?page=9&annotation=8JIE5M4R) 
  
 <mark class="hltr-purple">"4. Experimental Setup"</mark> [Page 10](zotero://open-pdf/library/items/CQJWWM37?page=10&annotation=EZS33VIU) 
  
 <mark class="hltr-purple">"4.1. Pretraining"</mark> [Page 10](zotero://open-pdf/library/items/CQJWWM37?page=10&annotation=2WNQCWW5) 
  
 <mark class="hltr-purple">"4.2. Post-training"</mark> [Page 12](zotero://open-pdf/library/items/CQJWWM37?page=12&annotation=ZK2AXTDI) 
  
 <mark class="hltr-purple">"5. Experimental Results"</mark> [Page 13](zotero://open-pdf/library/items/CQJWWM37?page=13&annotation=K22PECWQ) 
  
 <mark class="hltr-purple">"5.1. Main Results"</mark> [Page 13](zotero://open-pdf/library/items/CQJWWM37?page=13&annotation=IJ4JFP76) 
  
 <mark class="hltr-purple">"5.2. Model and Data Ablations"</mark> [Page 17](zotero://open-pdf/library/items/CQJWWM37?page=17&annotation=LLGDQNCN) 
  
 <mark class="hltr-purple">"6. Discussion and Future Work"</mark> [Page 18](zotero://open-pdf/library/items/CQJWWM37?page=18&annotation=FF8R2HWU) 
  
 <mark class="hltr-orange">"scaling laws for WAMs depending on the model size, dataset size, and the training compute need to be explored to determine the optimal configuration to extract the maximal capability of WAMs"</mark> [Page 18](zotero://open-pdf/library/items/CQJWWM37?page=18&annotation=SBPWPYKN) 
  
 <mark class="hltr-orange">"our experiments are still constrained to small scale in-lab data (only 12 minutes)."</mark> [Page 18](zotero://open-pdf/library/items/CQJWWM37?page=18&annotation=PY3LXITU) 
  
 <mark class="hltr-orange">"DreamZero is still computationally expensive due the large parameter size and the iterative denoising nature of video models"</mark> [Page 18](zotero://open-pdf/library/items/CQJWWM37?page=18&annotation=9NK2TNTP) 
  
 <mark class="hltr-yellow">"it is currently short-horizon (6 seconds). Robust long-horizon execution will require either a System 2 planner or WAMs with significantly extended context  18 World Action Models are Zero-shot Policies  windows."</mark> [Page 18](zotero://open-pdf/library/items/CQJWWM37?page=18&annotation=VBWUANZ6) 
  
 <mark class="hltr-orange">"it inherits limitations common to behavior cloning on tasks requiring sub-centimeter precision, such as key insertion or fine assembly."</mark> [Page 19](zotero://open-pdf/library/items/CQJWWM37?page=19&annotation=86R28AGQ) 
  
 <mark class="hltr-yellow">"That said, recent work (Kim et al., 2026) showed promising results that WAMs may actually hold an advantage for high-precision manipulation tasks with millimeter tolerance,"</mark> [Page 19](zotero://open-pdf/library/items/CQJWWM37?page=19&annotation=NMBIUZZK) 
  
 <mark class="hltr-orange">"(1) Degrees of freedom: Higher-DOF robots will require more play data to learn an accurate implicit IDM, as the mapping from visual futures to motor commands grows combinatorially with kinematic complexity."</mark> [Page 19](zotero://open-pdf/library/items/CQJWWM37?page=19&annotation=IY86YBPD) 
  
 <mark class="hltr-orange">"(2) Human similarity: Embodiments that more closely resemble humans—particularly humanoids with dexterous manipulation capabilities—may transfer more efficiently despite higher DOF, as they can leverage both the motion priors from video pretraining and the massive scale of human egocentric videos."</mark> [Page 19](zotero://open-pdf/library/items/CQJWWM37?page=19&annotation=ALVFIB7X) 
  
 <mark class="hltr-purple">"A. Comparison with Alternative World Model Architectures"</mark> [Page 20](zotero://open-pdf/library/items/CQJWWM37?page=20&annotation=7FYRZKUU) 
  
 <mark class="hltr-purple">"B. Bidirectional vs. Autoregressive WAMs"</mark> [Page 20](zotero://open-pdf/library/items/CQJWWM37?page=20&annotation=VBTM2Y66) 
  
 <mark class="hltr-purple">"C. Model and Training details"</mark> [Page 21](zotero://open-pdf/library/items/CQJWWM37?page=21&annotation=MFZQE6DC) 
  
 <mark class="hltr-purple">"D. Real-time Execution Details"</mark> [Page 22](zotero://open-pdf/library/items/CQJWWM37?page=22&annotation=Y4DBNVEP) 
  
 <mark class="hltr-purple">"D.1. System-level Optimizations"</mark> [Page 22](zotero://open-pdf/library/items/CQJWWM37?page=22&annotation=N6M7QXZA) 
  
 <mark class="hltr-purple">"D.2. Implementation-level Optimizations"</mark> [Page 23](zotero://open-pdf/library/items/CQJWWM37?page=23&annotation=9DSGCNSY) 
  
 <mark class="hltr-purple">"D.3. Model-level Optimizations — DreamZero-Flash"</mark> [Page 23](zotero://open-pdf/library/items/CQJWWM37?page=23&annotation=XSNEHVUB) 
  
 <mark class="hltr-purple">"E. AgiBot Diverse Data Collection Strategy"</mark> [Page 24](zotero://open-pdf/library/items/CQJWWM37?page=24&annotation=BQZ2JE9R) 
  
 <mark class="hltr-purple">"E.1. Daily Collection Workflow"</mark> [Page 24](zotero://open-pdf/library/items/CQJWWM37?page=24&annotation=D3F4RPZF) 
  
 <mark class="hltr-purple">"E.2. Multi-Task Episode Structure"</mark> [Page 24](zotero://open-pdf/library/items/CQJWWM37?page=24&annotation=BWU85Q3S) 
  
 <mark class="hltr-purple">"F. AgiBot Evaluation Details"</mark> [Page 25](zotero://open-pdf/library/items/CQJWWM37?page=25&annotation=2WEZ69A8) 
  
 <mark class="hltr-purple">"G. DROID Evaluation Details"</mark> [Page 25](zotero://open-pdf/library/items/CQJWWM37?page=25&annotation=MTSPLBJV) 
  
 <mark class="hltr-purple">"H. Failure Case Analysis"</mark> [Page 28](zotero://open-pdf/library/items/CQJWWM37?page=28&annotation=GHL4CQDE) 
  
 <mark class="hltr-gray">"Cosmos policy: Fine-tuning video models for visuomotor control and planning"</mark> [Page 34](zotero://open-pdf/library/items/CQJWWM37?page=34&annotation=RHN9ID5R) 
  
