---
created: March 31st 2026
categories:
  - "[[Concepts]]"
modified: March 31st 2026, 4:40:18 pm
tags:
---

The particle filter algorithm is a continuous cycle of prediction, measurement, and resampling. 

1. **Initialization:** Start by assuming a uniform particle distribution over the entire environment. Take $M$ samples of the initial state $s_0$ and weight each with an equal importance factor $w_t^{[m]} = 1/M$.
2. **Motion Prediction (Predict):** Upon robot motion control $u_t$, the particle state $s_t^{[m]}$ is estimated based on the motion model. As the robot moves, this motion probability distribution is applied to all particles. 
    - *Formula:* $\overline{bel}(s_t^{[m]}) = p(s_t^{[m]}|u_t, s_{t-1}^{[m]})$.
3. **Measurement / Importance Factor (Measure):** Upon robot sensing, a measurement probability is computed for each particle to calculate its importance factor. This factor is the probability of observing measurement $z_t$ for particle $s_t^{[m]}$ [2]. This process assigns non-uniform importance weights to the particle sets based on what the sensor "sees" (e.g. wall vs. no wall) [6, 8, 9].
    - *Formula:* $w_t^{[m]} = p(z_t |s_t^{[m]})$ [2, 7].
4. **Resampling (Update):** The particle state distribution is resampled and replaced proportionally to their state likelihood [1, 10]. This refocuses the particle set to regions in the state space with the highest posterior probability, drawing new samples at cells with the highest probabilities while keeping the same total number of particles [11-13].
    - *Formula:* $bel(s_t^{[m]}) = p(s_t^{[m]}|z_t) = w_t^{[m]} \overline{bel}(s_t^{[m]})$ [7].
    - *Orientation Note:* When resampling, generating random particle orientations produces more diverse variations in motion predictions, which is critical since measurements are relative to the robot's orientation [14, 15].
