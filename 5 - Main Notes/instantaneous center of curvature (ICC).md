---
categories:
  - "[[Formulas]]"
created: February 3rd 2026
modified: February 3rd 2026, 4:07:05 pm
tags:
  - robot-kinematics
  - wheeled-robot
formula: <math xmlns="http://www.w3.org/1998/Math/MathML"><mrow><mi>I</mi><mi>C</mi><mi>C</mi><mo>=</mo><mo form="prefix" stretchy="false">(</mo><mi>x</mi><mo>&#x2212;</mo><mi>R</mi><mi>sin</mi><mo form="prefix" stretchy="false">(</mo><mi>&#x3b8;</mi><mo form="postfix" stretchy="false">)</mo><mo separator="true">,</mo><mi>y</mi><mo>+</mo><mi>R</mi><mi>cos</mi><mo form="prefix" stretchy="false">(</mo><mi>&#x3b8;</mi><mo form="postfix" stretchy="false">)</mo><mo form="postfix" stretchy="false">)</mo></mrow></math>
---
# Overview
- *Definition:* the center around which the robot is rotating (as long as wheels relative differential drive remains constant) with the [[instantaneous center of rotation (ICR)]]
$$
ICC = (x - R \sin(\theta), y + R \cos(\theta))
$$
# Variables
- $(x,y,\theta)$: current pose in [[inertial frame]]
- R: [[distance to rotation center at ICC]]