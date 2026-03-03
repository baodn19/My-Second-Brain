---
created: February 26th 2026
categories:
  - "[[Concepts]]"
modified: March 3rd 2026, 4:38:31 pm
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
# Predict, Measure, Update Pipeline
1. *Predict ($\overline{bel}(s_{t})$):* is the estimated probability of the robot being in state $s_{t}$ after control $u_{t}$, it corresponds to **prior probability**. Example:
	- *Notation:* $\overline{bel}(s_{t})=p(s_{t}|u_{t},s_{t-1})$
	- s = 1 (state of seeing a wall): p(s = 1) = 0.9
	- s = 0 (state of not seeing a wall): p(s = 0) = 0.1
2. *Measure:* use the **sensor model**. Example:
	- z = 1 (sensor seeing a wall): p(z = 1 | s =1) = 0.7 (**True Positives**)
	- z = 0 (sensor not seeing a wall): p(z = 0 | s = 0) = 0.6 (**True Negatives**)
3. *Update:* use the [[Bayes Theorem]], the prosterior probabilities p(s|z) are proportional to p(z|s)p(s)
	- s: robot pose
	- z: sensor measurements
$$
p(s|z) \propto p(z|s)p(s) \implies p(s|z) = p(z|s)p(s)
$$
4. *Normalize:* scale the $p(s|z)$ so that they satisfy [[law of total probability]]
5. *[[Markov Decision Process (MDP)]]:* use the latest normalized states to repeat the pipeline, instead of remembering the whole history of states
- [[Hidden Markov Model (HMM)]]: we don't have a direct way to observe the value, rather the prosterior is the hidden value $p(s|z)$ while the $p(z|s)$ and $p(s)$ is visible