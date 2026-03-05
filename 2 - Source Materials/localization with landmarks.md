---
created: March 5th 2026
categories:
  - "[[Concepts]]"
modified: March 5th 2026, 4:40:13 pm
tags:
  - localization
---
- *Application:* when measurements to landmarks are not precise
- *Method:* 
	1. use [[normal distribution]] to find the probability (p(z|s)) of the robot measurement (z) given the robot state (s). Assume: 
	- the distance between the state and each landmark the mean: $D =\sqrt{ (\Delta x)^2+(\Delta y)^2 }$
	- the robot measurement is the state variable
	- standard deviation is manually set
$$

$$
	1. q