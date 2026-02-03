---
created: February 3rd 2026
categories:
  - "[[Formulas]]"
modified: February 3rd 2026, 4:37:56 pm
tags:
  - robot-kinematics
  - wheeled-robot
formula: <math xmlns="http://www.w3.org/1998/Math/MathML"><mrow><mi>k</mi><mo>=</mo><mfrac><mrow><mfenced open='|' close='|'><mi>&#x2207;</mi><msup><mi>f</mi><mo>&#x27c2;</mo></msup><mo>&#xb7;</mo><mi>H</mi><mi>f</mi><mo form="prefix" stretchy="false">(</mo><mi>&#x2207;</mi><msup><mi>f</mi><mo>&#x27c2;</mo></msup><msup><mo form="postfix" stretchy="false">)</mo><mi>T</mi></msup></mfenced></mrow><mrow><mi>&#x2016;</mi><mi>&#x2207;</mi><mi>f</mi><msup><mi>&#x2016;</mi><mn>3</mn></msup></mrow></mfrac></mrow></math>
---
# Overview
- *Definition:* The curvature (k) of a path or curve (C) is defined as the measurement of how much the curve is “bending” at point P
- *Simple:*
$$
k=\frac{1}{R}=\frac{\omega}{v}
$$
- *From any given shape (function):*
$$
k = \frac{\left| \nabla f^\perp \cdot Hf (\nabla f^\perp)^T \right|}{\|\nabla f\|^3}
$$
# Variables
## Simple
- R: [[distance to rotation center at ICC]]
- v: [[wheeled-robot linear velocity]]
- $\omega$:[[wheeled-robot angular velocity]]

## From any given shape (function)
- $\nabla f$: [[gradient]]
- 