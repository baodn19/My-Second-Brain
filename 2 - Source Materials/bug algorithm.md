---
created: February 17th 2026
categories:
  - "[[Concepts]]"
modified: February 17th 2026, 3:50:58 pm
tags:
  - motion-planning
---
- *Definition:* considers the robot as a single point, or “bug”, and computes a collision free path connecting the start and goal locations.
- *[[Frame of Reference]]:* 
	- [[inertial frame]]: knowing locations of objects, in the global frame of reference
	- [[robot frame]]: knowing locations of objects relative to the robot frame of reference
- *Behavior:*
	- [[Obstacle Avoidance]]: LiDar
	- [[Motion-To-Goal]]: need inertial frame information, use camera
- *[[finite-state machine (FSM)]]*:
![[bug algorithm state machine.png]]
