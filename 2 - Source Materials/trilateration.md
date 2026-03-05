---
created: March 5th 2026
categories:
  - "[[Concepts]]"
modified: March 5th 2026, 4:03:03 pm
tags:
  - localization
---
- *Definition:* localization based on the determination of absolute or relative measured distances to at least 3 known beacon or landmark locations.
- *Method:* Intersection of 3 circles formed by the distances r1, r2, r3, of the robot to the 3 beacons.
	1. *System of equations:* 
$$
\left\{\begin{array}{left}  C_{1}:(x-x_{1})^2+(y-y_{1})^2=r_{1}^2\\ C_{2}:(x-x_{2})^2+(y-y_{2})^2=r_{2}^2 \\ C_{3}:(x-x_{3})^2+(y-y_{3})^2=r_{3}^2 \\  \end{array}\right.
$$
		- $(x_{i},y_{i})$: position of landmark
		- $r_{i}$: distance from landmark to robot
	2. Generate two lines. Get a [[line equation]] by subtracting 2 [[circle equation]]s 
	3. Find the robot's coordinate by intersecting two lines