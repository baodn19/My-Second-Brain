---
categories:
  - "[[Concepts]]"
created: February 24th 2026
modified: February 24th 2026, 4:09:15 pm
tags:
  - motion-planning
---
- *Function:* go around obstacles and tries to reach the goal
- *Condition:*
	- *Initiation:* when robot reaches a point M that minimizes the distance to the goal, and new  $O_{i}$ take the robot further away from the goal ($d_{min}=d(M,q_{goal})$)
	- *Stop:* 
		- whether the [[interval of continuity]] intersects the line towards the goal
		- whether the distance to the goal: $d(x,q_{goal})<d_{min}$