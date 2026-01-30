---
created: January 27th 2026
modified: January 30th 2026, 3:28:54 pm
categories:
  - "[[Formulas]]"
tags:
  - linear-algebra
  - robot-kinematics
formula: "<math xmlns=\"http://www.w3.org/1998/Math/MathML\">\r  <mrow>\r    <mi>R</mi>\r    <mo stretchy=\"false\">(</mo>\r    <mi>&#x03B8;</mi>\r    <mo stretchy=\"false\">)</mo>\r    <mo>=</mo>\r    <mrow>\r      <mo>[</mo>\r      <mtable>\r        <mtr>\r          <mtd><mi>cos</mi><mo stretchy=\"false\">(</mo><mi>&#x03B8;</mi><mo stretchy=\"false\">)</mo></mtd>\r          <mtd><mi>sin</mi><mo stretchy=\"false\">(</mo><mi>&#x03B8;</mi><mo stretchy=\"false\">)</mo></mtd>\r          <mtd><mn>0</mn></mtd>\r        </mtr>\r        <mtr>\r          <mtd><mo>&#x2212;</mo><mi>sin</mi><mo stretchy=\"false\">(</mo><mi>&#x03B8;</mi><mo stretchy=\"false\">)</mo></mtd>\r          <mtd><mi>cos</mi><mo stretchy=\"false\">(</mo><mi>&#x03B8;</mi><mo stretchy=\"false\">)</mo></mtd>\r          <mtd><mn>0</mn></mtd>\r        </mtr>\r        <mtr>\r          <mtd><mn>0</mn></mtd>\r          <mtd><mn>0</mn></mtd>\r          <mtd><mn>1</mn></mtd>\r        </mtr>\r      </mtable>\r      <mo>]</mo>\r    </mrow>\r  </mrow>\r</math>"
---
# Overview
- *Definition:* a [[transformation matrix]] that is used to perform a [[rotation]] in [[Euclidean space]].
$$
R(\theta) = \begin{bmatrix} \cos(\theta) & \sin(\theta) & 0 \\ -\sin(\theta) & \cos(\theta) & 0 \\ 0 & 0 & 1 \end{bmatrix}
$$
# Variables
- $R(\theta)$: rotation matrix
- $\theta$: an angle about the origin of a two-dimensional [[Cartesian coordinate system]]