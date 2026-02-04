---
categories:
  - "[[Concepts]]"
created: February 3rd 2026
modified: February 4th 2026, 11:10:22 am
tags:
  - computer-vision
  - object-detection
  - machine-learning
---
- *Definition:* graphical representation of the trade-off between precision and recall for different classification thresholds
- *Use case:* imbalanced class distribution; focus on minority class and ignore True Negative; use [[receiver operating characteristic (ROC) curve]] for [[balanced class distribution]] 
- *Components:* calculated based on outcomes of a [[confusion matrix]]: True Positives (TP), False Positives (FP), and False Negatives (FN)
	- *Precision:* Of all the instances the model predicted as positive, how many were actually correct?
$$
Precision=\frac{TP}{TP+FP}
$$
	- *Recall:* Of all the actual positive instances in the data, how many did the model correctly identify?
$$
Recall=\frac{TP}{TP + FN}
$$
- *[[confidence threshold]]*: The curve generates PR value for every possible threshold from 0 to 1.
- *Shapes:* jagged because TP & FP don't always change linearly as threshold changes
	- *Perfect:* horizontal line with precision = 1 & recall = 1
	- *Bowed (high & right):* strong model; maintain high precision as recall increase $\implies$ [[average precision (AP)]], the area under the curve, represent the model's performance across all possible thresholds
	- *Steep Drop-off:* suggest more guessing as recall increase, lead to higher false positive