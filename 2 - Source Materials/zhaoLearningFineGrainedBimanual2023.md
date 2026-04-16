---
title: "[[Learning Fine-Grained Bimanual Manipulation with Low-Cost Hardware]]"
year: 2023
authors: Tony Z. Zhao, Vikash Kumar, Sergey Levine, Chelsea Finn
categories:
  - "[[Research References]]"
tags:
  - Computer-Science---Robotics
  - Computer-Science---Machine-Learning
modified: April 16th 2026, 4:37:17 pm
---

Zotero PDF Link: [[Zotero Attachments/Zhao et al. - 2023 - Learning Fine-Grained Bimanual Manipulation with Low-Cost Hardware.pdf]]
Related:  
# In-text annotations 
 <mark class="hltr-purple">"Abstract"</mark> [Page 1](zotero://open-pdf/library/items/8N9LEXHQ?page=1&annotation=TLX46EV8) 
  
 <mark class="hltr-purple">"I. INTRODUCTION"</mark> [Page 1](zotero://open-pdf/library/items/8N9LEXHQ?page=1&annotation=I8VT5JRS) 
  
 <mark class="hltr-purple">"II. RELATED WORK"</mark> [Page 2](zotero://open-pdf/library/items/8N9LEXHQ?page=2&annotation=PWKJ6N9E) 
  
 <mark class="hltr-purple">"III. ALOHA: A LOW-COST OPEN-SOURCE HARDWARE  SYSTEM FOR BIMANUAL TELEOPERATION"</mark> [Page 3](zotero://open-pdf/library/items/8N9LEXHQ?page=3&annotation=KZJTKZYY) 
  
 <mark class="hltr-purple">"IV. ACTION CHUNKING WITH TRANSFORMERS"</mark> [Page 4](zotero://open-pdf/library/items/8N9LEXHQ?page=4&annotation=E4ETKHKU) 
  
 <mark class="hltr-yellow">"the amount of force applied is implicitly defined by the difference between them, through the low-level PID controller"</mark> [Page 4](zotero://open-pdf/library/items/8N9LEXHQ?page=4&annotation=ANJGR7SI) 
  
 <mark class="hltr-yellow">"train ACT to predict the sequence of future actions"</mark> [Page 4](zotero://open-pdf/library/items/8N9LEXHQ?page=4&annotation=F6ECMH9K) 
  
 <mark class="hltr-yellow">"An action here corresponds to the target joint positions for both arms in the next time step."</mark> [Page 4](zotero://open-pdf/library/items/8N9LEXHQ?page=4&annotation=2UGN3J2H) 
  
 <mark class="hltr-yellow">"imitate what a human operator would do in the following time steps given current observations."</mark> [Page 4](zotero://open-pdf/library/items/8N9LEXHQ?page=4&annotation=DF8QNR7G) 
  
 <mark class="hltr-yellow">"main challenge that arises is compounding errors, where errors from previous actions lead to states that are outside of training distribution."</mark> [Page 4](zotero://open-pdf/library/items/8N9LEXHQ?page=4&annotation=MRMPJRDK) 
  
 <mark class="hltr-purple">"A. Action Chunking and Temporal Ensemble"</mark> [Page 4](zotero://open-pdf/library/items/8N9LEXHQ?page=4&annotation=TU8JQCIU) 
  
 <mark class="hltr-yellow">"We are inspired by action chunking, a neuroscience concept where individual actions are grouped together and executed as one unit, making them more efficient to store and execute [35]"</mark> [Page 4](zotero://open-pdf/library/items/8N9LEXHQ?page=4&annotation=7FEEF73R) 
  
 <mark class="hltr-yellow">"Chunking can also help model non-Markovian behavior in human demonstrations."</mark> [Page 4](zotero://open-pdf/library/items/8N9LEXHQ?page=4&annotation=H9NJEBFL) 
 
What is Markovian behavior? [Page 4](zotero://open-pdf/library/items/8N9LEXHQ?page=4&annotation=H9NJEBFL) 
  
 <mark class="hltr-yellow">"a new environment observation is incorporated abruptly every k steps and can result in jerky robot motion."</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=GL9PJ55K) 
  
 <mark class="hltr-yellow">"Our temporal ensemble performs a weighted average over these predictions with an exponential weighting scheme wi = exp(−m ∗ i), where w0 is the weight for the oldest action."</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=8WASJ3RJ) 
  
 <mark class="hltr-yellow">"we aggregate actions predicted for the same timestep."</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=8Z24A4P9) 
  
 <mark class="hltr-purple">"B. Modeling human data"</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=5SGSWMQU) 
  
 <mark class="hltr-yellow">"train the policy as a conditional variational autoencoder (CVAE) [55], to generate an action sequence conditioned on current observations"</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=6R3VYCVC) 
  
 <mark class="hltr-yellow">"The CVAE encoder only serves to train the CVAE decoder (the policy) and is discarded at test time."</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=4G6M75SR) 
  
 <mark class="hltr-yellow">"a diagonal Gaussian"</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=QJQ99V5E) 
 
Is this the same as Kalman Filter? [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=QJQ99V5E) 
  
 <mark class="hltr-yellow">"The CVAE decoder, i.e. the policy, conditions on both z and the current observations (images + joint positions) to predict the action sequence."</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=H3AQK8UI) 
  
 <mark class="hltr-yellow">"a reconstruction loss and a term that regularizes the encoder to a Gaussian prior."</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=DWC4SZJL) 
  
 <mark class="hltr-purple">"C. Implementing ACT"</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=V6VNBMAZ) 
  
 <mark class="hltr-yellow">". The CVAE encoder is implemented with a BERT-like transformer encoder [13]."</mark> [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=F4GA9RTA) 
 
What is BERT-like transformer? [Page 5](zotero://open-pdf/library/items/8N9LEXHQ?page=5&annotation=F4GA9RTA) 
  
 <mark class="hltr-purple">"V. EXPERIMENTS"</mark> [Page 6](zotero://open-pdf/library/items/8N9LEXHQ?page=6&annotation=M8A89I6E) 
  
 <mark class="hltr-purple">"A. Tasks"</mark> [Page 6](zotero://open-pdf/library/items/8N9LEXHQ?page=6&annotation=UCX4M546) 
  
 <mark class="hltr-purple">"B. Data Collection"</mark> [Page 8](zotero://open-pdf/library/items/8N9LEXHQ?page=8&annotation=AH776JJJ) 
  
 <mark class="hltr-purple">"C. Experiment Results"</mark> [Page 8](zotero://open-pdf/library/items/8N9LEXHQ?page=8&annotation=3GLUGRCR) 
  
 <mark class="hltr-purple">"VI. ABLATIONS"</mark> [Page 9](zotero://open-pdf/library/items/8N9LEXHQ?page=9&annotation=Q3CMNPPZ) 
  
 <mark class="hltr-purple">"A. Action Chunking and Temporal Ensembling"</mark> [Page 9](zotero://open-pdf/library/items/8N9LEXHQ?page=9&annotation=IIVECMA6) 
  
 <mark class="hltr-purple">"B. Training with CVAE"</mark> [Page 9](zotero://open-pdf/library/items/8N9LEXHQ?page=9&annotation=I7VTXKVA) 
  
 <mark class="hltr-purple">"C. Is High-Frequency Necessary?"</mark> [Page 10](zotero://open-pdf/library/items/8N9LEXHQ?page=10&annotation=T7QAKS3W) 
  
 <mark class="hltr-purple">"VII. LIMITATIONS AND CONCLUSION"</mark> [Page 10](zotero://open-pdf/library/items/8N9LEXHQ?page=10&annotation=8KJIGG53) 
  
 <mark class="hltr-purple">"ACKNOWLEDGEMENT"</mark> [Page 10](zotero://open-pdf/library/items/8N9LEXHQ?page=10&annotation=4NIBULDY) 
  
