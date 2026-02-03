---
created: January 27th 2026
modified: February 3rd 2026, 3:59:03 pm
categories:
  - "[[Formulas]]"
tags:
  - robot-kinematics
  - wheeled-robot
formula: <math xmlns="http://www.w3.org/1998/Math/MathML"><mrow><msub><mi>v</mi><mi>l</mi></msub><mo>=</mo><mi>r</mi><msub><mi>&#x3c6;</mi><mi>l</mi></msub><mo>=</mo><mi>&#x3c9;</mi><mrow><mfenced open='(' close=')'><mi>R</mi><mo>&#x2212;</mo><mfrac><mi>d</mi><mn>2</mn></mfrac></mfenced></mrow></mrow></math>
---
# Overview
- *Definition:* linear velocity of left wheel
$$
v_l = r\varphi_{l} = \omega \left( R - \frac{d}{2} \right)
$$
# Variables
- $v_{l}$: left wheel linear velocity
- $\omega$: [[wheeled-robot angular velocity]]
- $d$: distance between wheels (axis length)
- r: radius of wheel
- R: distance to rotation center at [[instantaneous center of curvature (ICC)]]
- $\varphi_{l}$: left [[wheel angular velocity]]