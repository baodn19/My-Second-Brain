---
categories:
  - "[[Formulas]]"
created: February 3rd 2026
modified: February 3rd 2026, 4:16:55 pm
tags:
  - robot-kinematics
  - wheeled-robot
formula: "<math xmlns=\"http://www.w3.org/1998/Math/MathML\" display=\"block\">\r  <mrow>\r    <mrow>\r      <mo>[</mo>\r      <mtable>\r        <mtr>\r          <mtd>\r            <msub>\r              <mi>x</mi>\r              <mi>c</mi>\r            </msub>\r          </mtd>\r        </mtr>\r        <mtr>\r          <mtd>\r            <msub>\r              <mi>y</mi>\r              <mi>c</mi>\r            </msub>\r          </mtd>\r        </mtr>\r        <mtr>\r          <mtd>\r            <msub>\r              <mi>&#x3B8;</mi>\r              <mi>c</mi>\r            </msub>\r          </mtd>\r        </mtr>\r      </mtable>\r      <mo>]</mo>\r    </mrow>\r    <mo>=</mo>\r    <mrow>\r      <mo>[</mo>\r      <mtable>\r        <mtr>\r          <mtd>\r            <mi>cos</mi>\r            <mo>(</mo>\r            <mi>&#x3C9;</mi>\r            <mi>t</mi>\r            <mo>)</mo>\r          </mtd>\r          <mtd>\r            <mo>&#x2212;</mo>\r            <mi>sin</mi>\r            <mo>(</mo>\r            <mi>&#x3C9;</mi>\r            <mi>t</mi>\r            <mo>)</mo>\r          </mtd>\r          <mtd>\r            <mn>0</mn>\r          </mtd>\r        </mtr>\r        <mtr>\r          <mtd>\r            <mi>sin</mi>\r            <mo>(</mo>\r            <mi>&#x3C9;</mi>\r            <mi>t</mi>\r            <mo>)</mo>\r          </mtd>\r          <mtd>\r            <mi>cos</mi>\r            <mo>(</mo>\r            <mi>&#x3C9;</mi>\r            <mi>t</mi>\r            <mo>)</mo>\r          </mtd>\r          <mtd>\r            <mn>0</mn>\r          </mtd>\r        </mtr>\r        <mtr>\r          <mtd>\r            <mn>0</mn>\r          </mtd>\r          <mtd>\r            <mn>0</mn>\r          </mtd>\r          <mtd>\r            <mn>1</mn>\r          </mtd>\r        </mtr>\r      </mtable>\r      <mo>]</mo>\r    </mrow>\r    <mrow>\r      <mo>[</mo>\r      <mtable>\r        <mtr>\r          <mtd>\r            <mi>x</mi>\r            <mo>&#x2212;</mo>\r            <msub>\r              <mi>ICC</mi>\r              <mi>x</mi>\r            </msub>\r          </mtd>\r        </mtr>\r        <mtr>\r          <mtd>\r            <mi>y</mi>\r            <mo>&#x2212;</mo>\r            <msub>\r              <mi>ICC</mi>\r              <mi>y</mi>\r            </msub>\r          </mtd>\r        </mtr>\r        <mtr>\r          <mtd>\r            <mi>&#x3B8;</mi>\r          </mtd>\r        </mtr>\r      </mtable>\r      <mo>]</mo>\r    </mrow>\r    <mo>+</mo>\r    <mrow>\r      <mo>[</mo>\r      <mtable>\r        <mtr>\r          <mtd>\r            <msub>\r              <mi>ICC</mi>\r              <mi>x</mi>\r            </msub>\r          </mtd>\r        </mtr>\r        <mtr>\r          <mtd>\r            <msub>\r              <mi>ICC"
---
# Overview
- *Definition:* determining a mobile robot's pose based on [[wheeled-robot angular velocity]]
$$
\begin{bmatrix} x_c \\ y_c \\ \theta_c \end{bmatrix} = \begin{bmatrix} \cos(\omega t) & -\sin(\omega t) & 0 \\ \sin(\omega t) & \cos(\omega t) & 0 \\ 0 & 0 & 1 \end{bmatrix} \begin{bmatrix} x - ICC_x \\ y - ICC_y \\ \theta \end{bmatrix} + \begin{bmatrix} ICC_x \\ ICC_y \\ \omega t \end{bmatrix}
$$
- Rotation transformation is only possible when both [[inertial frame]] and [[robot frame]] match, which is at the origin point => We need the translation steps
# Variables
- $(x_{c},y_{c},\theta_{c})$: final robot pose in [[inertial frame]]
- $\omega$: [[wheeled-robot angular velocity]]
- t: time traveled
- $(ICC_{x}, ICC_{y})$: [[instantaneous center of curvature (ICC)]]