---
categories:
  - "[[Formulas]]"
created: February 3rd 2026
modified: February 11th 2026, 10:15:29 am
tags:
  - wheeled-robot
  - robot-kinematics
formula: <math xmlns="http://www.w3.org/1998/Math/MathML"><mrow><mi>R</mi><mo>=</mo><mfrac><mrow><msub><mi>d</mi><mrow><mi>a</mi><mi>x</mi><mi>i</mi><mi>s</mi></mrow></msub><mo form="prefix" stretchy="false">(</mo><msub><mi>v</mi><mi>r</mi></msub><mo>+</mo><msub><mi>v</mi><mi>l</mi></msub><mo form="postfix" stretchy="false">)</mo></mrow><mrow><mn>2</mn><mo form="prefix" stretchy="false">(</mo><msub><mi>v</mi><mi>r</mi></msub><mo>&#x2212;</mo><msub><mi>v</mi><mi>l</mi></msub><mo form="postfix" stretchy="false">)</mo></mrow></mfrac></mrow></math>
---
# Overview
- *Definition:* distance to rotation center at ICC when mobile robot is turning
$$
R=\frac{d_{axis}(v_{r}+v_{l})}{2(v_{r}-v_{l})}
$$

# Variables
- $d_{axis}$: distance between 2 wheels
- $v_{r}$: [[right wheel linear velocity]]
- $v_{l}$: [[left wheel linear velocity]]