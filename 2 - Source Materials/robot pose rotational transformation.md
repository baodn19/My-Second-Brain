---
created: January 29th 2026
categories:
  - "[[Formulas]]"
modified: February 3rd 2026, 3:56:55 pm
tags:
  - robot-kinematics
  - wheeled-robot
formula: <math xmlns="http://www.w3.org/1998/Math/MathML"><mrow><mfenced open='[' close=']'><mtable columnalign="center&#xA0;center" class="tml-array"><mtr><mtd><mrow><mi>x</mi><mi>cos</mi><mo form="prefix" stretchy="false">(</mo><mi>&#x3b8;</mi><mo form="postfix" stretchy="false">)</mo><mo>+</mo><mi>y</mi><mi>sin</mi><mo form="prefix" stretchy="false">(</mo><mi>&#x3b8;</mi><mo form="postfix" stretchy="false">)</mo></mrow></mtd></mtr><mtr><mtd><mrow><mo>&#x2212;</mo><mi>x</mi><mi>sin</mi><mo form="prefix" stretchy="false">(</mo><mi>&#x3b8;</mi><mo form="postfix" stretchy="false">)</mo><mo>+</mo><mi>y</mi><mi>cos</mi><mo form="prefix" stretchy="false">(</mo><mi>&#x3b8;</mi><mo form="postfix" stretchy="false">)</mo></mrow></mtd></mtr><mtr><mtd><mi>&#x3b8;</mi></mtd></mtr></mtable></mfenced></mrow></math>
---
# Overview
- *Definition:* robot pose from [[inertial frame]] to [[robot frame]] when the robot turns [[counter clockwise]] 
$$
p_R = R(\theta ) \cdot \left[\begin{array}{cc} x & y & \theta  \\  \end{array}\right]^T
\iff \begin{bmatrix} x_R \\ y_R \\ \theta_R \\  \end{bmatrix} = \begin{bmatrix} \cos (\theta ) & \sin (\theta ) & 0 \\ - \sin (\theta ) & \cos (\theta ) & 0 \\ 0 & 0 & 1 \\  \end{bmatrix}\begin{bmatrix} x \\ y \\ \theta  \\  \end{bmatrix} = \begin{bmatrix}x\cos (\theta ) + y\sin (\theta ) \\ - x\sin (\theta ) + y\cos (\theta ) \\ \theta  \\  \end{bmatrix}
$$
- Robot pose from [[robot frame]] to [[inertial frame]] 
$$
\left[\begin{array}{cc} x & y & \theta  \\  \end{array}\right]^T = R(\theta )^{-1} \cdot \left[\begin{array}{cc} x_{R} & y_{R} & \theta_{R}  \\  \end{array}\right]^T
\iff \begin{bmatrix} x \\ y \\ \theta \\  \end{bmatrix} = \begin{bmatrix}x_{R}\cos (\theta ) - y_{R}\sin (\theta ) \\  x_{R}\sin (\theta ) + y_{R}\cos (\theta ) \\ \theta_{R}  \\  \end{bmatrix}
$$
# Variables
- $R(\theta)$: [[Rotation Matrix in Z-axis]]
- $p_{R}$: robot pose in [[robot frame]]
- $(x, y, \theta)$: [[inertial frame]] coordinate
- $(x_{R},y_{R},\theta_{R})$: [[robot frame]] coordinate