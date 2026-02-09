---
categories:
  - "[[Concepts]]"
created: February 6th 2026
modified: February 9th 2026, 1:53:26 pm
tags:
  - machine-learning
  - computer-vision
---
- *Definition:* the proportion of the overlapping area between the human annotated box and the prediction box to the total area of both boxes
$$
IoU=\frac{Area OfOverlap(Intersection)}{Total AreaOfBothBoxes(Union)}
$$
- *Value:*
	- **IoU = 0:** Complete miss. The boxes don't touch at all.
	- **IoU = 0.5:** "Good enough." This is the standard passing grade for many competitions. The boxes overlap significantly, but it's not a perfect fit.
	- **IoU = 0.9:** Excellent. The predicted box is almost identical to the ground truth.
	- **IoU = 1:** Impossible perfection. The boxes are pixel-perfect matches.