---
created: January 29th 2026
categories:
  - "[[Formulas]]"
modified: January 29th 2026, 4:33:56 pm
tags:
  - robot-kinematics
  - wheeled-robot
formula: "<math xmlns=\"http://www.w3.org/1998/Math/MathML\">\r  <mrow>\r    <msub>\r      <mover>\r        <mi>&#x03BE;</mi>\r        <mo>&#x02D9;</mo>\r      </mover>\r      <mi>R</mi>\r    </msub>\r    <mo>=</mo>\r    <mi>R</mi>\r    <mo stretchy=\"false\">(</mo>\r    <mi>&#x03B8;</mi>\r    <mo stretchy=\"false\">)</mo>\r    <mo>&#x22C5;</mo>\r    <msub>\r      <mover>\r        <mi>&#x03BE;</mi>\r        <mo>&#x02D9;</mo>\r      </mover>\r      <mi>I</mi>\r    </msub>\r    <mo>=</mo>\r    <mi>R</mi>\r    <mo stretchy=\"false\">(</mo>\r    <mi>&#x03B8;</mi>\r    <mo stretchy=\"false\">)</mo>\r    <mo>&#x22C5;</mo>\r    <msup>\r      <mrow>\r        <mo>[</mo>\r        <mtable>\r          <mtr>\r            <mtd>\r              <mover>\r                <mi>x</mi>\r                <mo>&#x02D9;</mo>\r              </mover>\r            </mtd>\r            <mtd>\r              <mover>\r                <mi>y</mi>\r                <mo>&#x02D9;</mo>\r              </mover>\r            </mtd>\r            <mtd>\r              <mover>\r                <mi>&#x03B8;</mi>\r                <mo>&#x02D9;</mo>\r              </mover>\r            </mtd>\r          </mtr>\r        </mtable>\r        <mo>]</mo>\r      </mrow>\r      <mi>T</mi>\r    </msup>\r  </mrow>\r</math>"
---
# Overview
- *Definition:* robot velocity transformation from [[inertial frame]] to [[robot frame]] ([[inverse kinematic]])
$$
\dot{\xi}_R = R(\theta) \cdot \dot{\xi}_I = R(\theta) \cdot [\dot{x} \quad \dot{y} \quad \dot{\theta}]^T = [v_x \quad v_y \quad \omega]^T = f(\dot{x}, \dot{y}, \dot{\theta})
$$
- *[[forward kinematics]]*: robot velocity transformation from [[robot frame]] to [[inertial frame]]
$$
\dot{\xi}_I = [\dot{x} \quad \dot{y} \quad \dot{\theta}]^T = f(v, \omega)
$$
# Variables
- $R(\theta)$: [[Rotation Matrix in Z-axis]]
- $\dot{\xi}_R$: robot velocity in robot frame
- $\dot{\xi}_I$: robot velocity in inertial frame
- $(\dot{x}, \dot{y})$: Translation Velocities
- $\dot{\theta}$: Rotation Velocity
- $(v_{x}, v_{y})$: robot linear velocity in the [[Cartesian coordinate system]]
- $\omega$: [[wheeled-robot angular velocity]]