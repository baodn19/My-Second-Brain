---
categories:
  - "[[Concepts]]"
created: February 19th 2026
modified: February 19th 2026, 4:06:42 pm
tags:
  - motion-planning
---
- *Raw distance [[function]]:* $\rho: R^2\times S^1\to R^1$
	- $R^2$: 2D robot locations;
	- $S^1$: 1D robot orientations
	- $R^1$: 1D distances sensed and sent back to the robot
- *Output:* $\rho(x, \theta)$ is the distance to the closest obstacle (or wall) along the ray from x at an angle $\theta$
	- $x \in R^2$: position of robot in the 2D space
	- $\theta \in S^1$: orientation of the robot
- *saturated raw distance function:*
$$
\rho_R(x, \theta) = \begin{cases} \rho(x, \theta), & \text{if } \rho(x, \theta) < R \\ \infty, & \text{otherwise} \end{cases}
$$
