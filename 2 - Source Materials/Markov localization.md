---
created: February 26th 2026
categories:
  - "[[Concepts]]"
modified: March 5th 2026, 4:23:02 pm
tags:
  - motion-planning
---
- *Methodology:* a discrete representation of the state space. The environment is represented by a finite number of states. At each iteration, the [[probability]] of each state of the entire space is updated.
- *Sensor model:* use [[confusion matrix]]
	- Example:

| x                | State "wall"       | State "no wall"    |
| ---------------- | ------------------ | ------------------ |
| Sensor "wall"    | **True Positives** | False Positives    |
| Sensor "no wall" | False Negatives    | **True Negatives** |
# [[Predict, Measure, Update Pipeline]]
