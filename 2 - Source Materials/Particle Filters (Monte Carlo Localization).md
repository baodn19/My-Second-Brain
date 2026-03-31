---
created: March 31st 2026
categories:
  - "[[Concepts]]"
modified: March 31st 2026, 4:38:29 pm
tags:
  - localization
  - particle_filters
---
- **Goal:** The goal of localization is to estimate the robot *state s*.
- **Definition:** Particle Filter, or Monte Carlo localization, is a Bayesian-based filter localization method that samples the complete workspace using a weight function derived from the belief distribution of the previous stage. Particle filters rely heavily on [[Monte Carlo methods]], using repeated random sampling to obtain numerical results.
- **Particles ($S_t$):** Each particle represents a belief or estimate of the robot state using random samples. $S_t$ represents the samples of a posterior particle distribution.
- **Hypothesis and Set:** Each particle $s_t^{[m]}$ is a hypothesis of what the true robot state may be at time $t$, where $m$ (an **index that identifies a specific, individual particle** within the entire set of particles (St​)) is an instantiation between $1$ and $M$. 
- **Representation:** The goal of this method is to approximate the posterior belief $bel(s_t)$ by the total set of particles $S_t$. For example, a filter might use $M = 10,000$ total particles to represent the space.
