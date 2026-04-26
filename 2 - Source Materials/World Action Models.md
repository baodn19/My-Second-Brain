---
categories:
  - "[[Concepts]]"
created: April 25th 2026
modified: April 25th 2026, 10:05:40 pm
tags:
  - robot-learning
---
- *Description:* robotics [[foundation models]] designed to jointly predict future visual states (video) and corresponding robot actions.
- **Mechanism:** WAMs shift policy learning from dense state-action imitation to inverse dynamics. They generate a visual plan of how the world will evolve and align motor commands to match that predicted visual future.
- **Foundation:** They are typically initialized from large-scale video diffusion models to inherit rich spatiotemporal and physical dynamics priors learned from internet-scale video data.
- *Latest models:*
	- **DREAMZERO:** from [[World Action Models are Zero-shot Policies]] by [[NVIDIA]]
	- 