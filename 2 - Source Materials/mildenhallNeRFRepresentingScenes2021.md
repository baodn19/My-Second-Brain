---
title: "NeRF: representing scenes as neural radiance fields for view synthesis"
year: 2021
authors: Ben Mildenhall, Pratul P. Srinivasan, Matthew Tancik, Jonathan T. Barron, Ravi Ramamoorthi, Ren Ng
categories:
  - "[[Research References]]"
tags:
  - Computing-methodologies
  - Computer-graphics
  - Image-manipulation
  - Image-based-rendering
pass: first
modified: January 29th 2026, 11:40:02 pm
---

Zotero PDF Link: [Mildenhall et al. - 2021 - NeRF representing scenes as neural radiance fields for view synthesis.pdf](zotero://select/library/items/HGHF9RJA) 
Related:  
# In-text annotations 
 <mark class="hltr-purple">"Abstract"</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=YN73IYUR) 
 
[[discretized voxel]] [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=YN73IYUR) 
  
 <mark class="hltr-purple">"1. INTRODUCTION"</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=IXSDH8FM) 
  
 <mark class="hltr-orange">"we address the long-standing problem of view synthesis in a new way."</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=DKZ6C6VT) 
  
 <mark class="hltr-gray">"View synthesis is the problem of rendering new views of a scene from a given set of input images and their respective camera poses."</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=EQPMBAEK) 
  
 <mark class="hltr-orange">"Producing photorealistic outputs from new viewpoints requires correctly handling complex geometry and material reflectance properties."</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=EFP3DDNI) 
  
 <mark class="hltr-yellow">"We represent a static scene as a continuous 5D function that outputs the radiance emitted in each direction (θ, φ) at each point (x, y, z) in space, and a density at each point which acts like a differential opacity controlling how much radiance is accumulated by a ray passing through (x, y, z)."</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=JRNBVAKX) 
  
 <mark class="hltr-yellow">"Our method optimizes a deep fully connected neural network without any convolutional layers"</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=5E2WRQFZ) 
  
 <mark class="hltr-yellow">"To render this neural radiance field (NeRF) from a particular viewpoint"</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=S7UGZJCJ) 
  
 <mark class="hltr-yellow">"1) march camera rays through the scene to generate a sampled"</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=EZPCPYFU) 
  
 <mark class="hltr-yellow">"set of 3D points, 2) use those points and their corresponding 2D viewing directions as input to the neural network to produce an output set of colors and densities, and 3) use classical volume rendering techniques to accumulate those colors and densities into a 2D image."</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=5LMRC5GP) 
  
 <mark class="hltr-magenta">"this process is naturally differentiable, we can use gradient descent to optimize this model by minimizing the error between each observed image and the corresponding views rendered from our representation."</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=AY4TMCAZ) 
 
What does it mean by naturally differentiable and how does gradient descent helps [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=AY4TMCAZ) 
  
 <mark class="hltr-orange">"basic implementation of optimizing a neural radiance field representation for a complex scene does not converge to a sufficiently high-resolution representation."</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=NW4P8QJD) 
  
 <mark class="hltr-yellow">"address this issue by transforming input 5D coordinates with a positional encoding that enables the MLP to represent higher frequency functions."</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=C24LMY5N) 
  
 <mark class="hltr-yellow">"Our approach can represent complex real-world geometry and appearance and is well suited for gradient-based optimization using projected images."</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=SI233KGY) 
  
 <mark class="hltr-yellow">"storing a scene in the parameters of a neural network, our method overcomes the prohibitive storage costs of discretized voxel grids when modeling complex scenes at high resolutions."</mark> [Page 99](zotero://open-pdf/library/items/HGHF9RJA?page=99&annotation=XA5V2ARK) 
  
 <mark class="hltr-purple">"2.2. View synthesis and image-based rendering"</mark> [Page 100](zotero://open-pdf/library/items/HGHF9RJA?page=100&annotation=7EB7MZ2B) 
  
 <mark class="hltr-purple">"2. RELATED WORK"</mark> [Page 100](zotero://open-pdf/library/items/HGHF9RJA?page=100&annotation=5NSK2P7E) 
  
 <mark class="hltr-purple">"2.1. Neural 3D shape representations"</mark> [Page 100](zotero://open-pdf/library/items/HGHF9RJA?page=100&annotation=YCAYLUFL) 
  
 <mark class="hltr-purple">"3. NEURAL RADIANCE FIELD SCENE REPRESENTATION"</mark> [Page 101](zotero://open-pdf/library/items/HGHF9RJA?page=101&annotation=YNSM2Z3Y) 
  
 <mark class="hltr-purple">"4. VOLUME RENDERING WITH RADIANCE FIELDS"</mark> [Page 101](zotero://open-pdf/library/items/HGHF9RJA?page=101&annotation=RKFJLDV4) 
  
 <mark class="hltr-purple">"5.2. Implementation details"</mark> [Page 102](zotero://open-pdf/library/items/HGHF9RJA?page=102&annotation=PV9E746K) 
  
 <mark class="hltr-purple">"6. RESULTS"</mark> [Page 102](zotero://open-pdf/library/items/HGHF9RJA?page=102&annotation=3KT2I8YX) 
  
 <mark class="hltr-purple">"6.1. Datasets"</mark> [Page 102](zotero://open-pdf/library/items/HGHF9RJA?page=102&annotation=6K4EM932) 
  
 <mark class="hltr-purple">"5. OPTIMIZING A NEURAL RADIANCE FIELD"</mark> [Page 102](zotero://open-pdf/library/items/HGHF9RJA?page=102&annotation=TDGVHMJD) 
  
 <mark class="hltr-purple">"5.1. Positional encoding"</mark> [Page 102](zotero://open-pdf/library/items/HGHF9RJA?page=102&annotation=FCYH7N2N) 
  
 <mark class="hltr-purple">"7. CONCLUSION"</mark> [Page 105](zotero://open-pdf/library/items/HGHF9RJA?page=105&annotation=XLR2NBPA) 
  
 <mark class="hltr-orange">"deficiencies of prior work that uses MLPs to represent objects and scenes as continuous functions."</mark> [Page 105](zotero://open-pdf/library/items/HGHF9RJA?page=105&annotation=28NVH6TC) 
  
 <mark class="hltr-yellow">"demonstrate that representing scenes as 5D neural radiance fields"</mark> [Page 105](zotero://open-pdf/library/items/HGHF9RJA?page=105&annotation=ST74KQKA) 
  
 <mark class="hltr-yellow">"produces better renderings than the previously dominant approach of training deep CNNs to output discretized voxel representations."</mark> [Page 105](zotero://open-pdf/library/items/HGHF9RJA?page=105&annotation=AQA2HFUD) 
  
 <mark class="hltr-purple">"6.2. Comparisons"</mark> [Page 105](zotero://open-pdf/library/items/HGHF9RJA?page=105&annotation=W7UU9T7H) 
  
 <mark class="hltr-purple">"6.3. Discussion"</mark> [Page 105](zotero://open-pdf/library/items/HGHF9RJA?page=105&annotation=5DQ8NKUM) 
  
