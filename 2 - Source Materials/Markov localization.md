---
created: February 26th 2026
categories:
  - "[[Concepts]]"
modified: February 26th 2026, 4:34:48 pm
tags:
  - motion-planning
---
- *Methodology:* a discrete representation of the state space. The environment is represented by a finite number of states. At each iteration, the [[probability]] of each state of the entire space is updated.
- Based on [[Bayes Theorem]], robot pose (s) is given by measurements z:
$$
P(s|z)=P(z|s) \frac{P(s)}{P(z)}
$$
- The prosterior probabilities P(s|z) are proportional to P(z|s)P(s)
	- This is the Update part in the pipeline of (Predict, Measure, Update)
- *Find the state's probability:* use [[law of total probability]] on previous robot pose
- *Sensor model:* use [[confusion matrix]]
	- Example:

| x                | State "wall"    | State "no wall" |
| ---------------- | --------------- | --------------- |
| Sensor "wall"    | True Positives  | False Positives |
| Sensor "no wall" | False Negatives | True Negatives  |
