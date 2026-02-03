---
categories:
  - "[[Concepts]]"
created: February 3rd 2026
modified: February 3rd 2026, 3:38:23 pm
tags:
  - computer-vision
  - object-detection
  - machine-learning
---
- *Definition:* graphical representation of the trade-off between precision and recall for different classification thresholds
- *Components:* calculated based on outcomes of a [[confusion matrix]]: True Positives (TP), False Positives (FP), and False Negatives (FN)
	- *Precision:* Of all the instances the model predicted as positive, how many were actually correct?
$$
Precision=\frac{TP}{TP+FP}
$$
	- *Recall:* Of all the actual positive instances in the data, how many did the model correctly identify?
$$
Recall=\frac{TP}{TP + FN}
$$
