---
categories:
  - "[[Concepts]]"
created: February 6th 2026
modified: February 8th 2026, 9:23:18 am
tags:
  - machine-learning
---
- *Definition:* visual summary of model's predictions compared to the actual ground truth
	- Identify exactly which classes your model is struggling with
	- Is it prone to "hallucinating" objects or missing them entirely
- *Binary logic:*
	- *True Positive (TP):* model predicted correctly (the diagonal line from top right to bottom left)
	- *True Negative (TN):* model correctly leaving out the background
	- *False Positive (FP):* model mistake something else as the class
	- *False Negative (FN):* model miss the class and label it as background or sth else