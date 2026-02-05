---
categories:
  - "[[Concepts]]"
  - "[[Formulas]]"
created: February 5th 2026
modified: February 5th 2026, 4:33:59 pm
tags:
  - control-system
formula: <math xmlns="http://www.w3.org/1998/Math/MathML"><mrow><msub><mi>K</mi><mi>d</mi></msub><mo>&#xb7;</mo><mo form="prefix" stretchy="false">[</mo><mi>e</mi><mo form="prefix" stretchy="false">(</mo><mi>t</mi><mo form="postfix" stretchy="false">)</mo><mo>&#x2212;</mo><mi>e</mi><mo form="prefix" stretchy="false">(</mo><mi>t</mi><mo>&#x2212;</mo><mn>1</mn><mo form="postfix" stretchy="false">)</mo><mo form="postfix" stretchy="false">]</mo><mo lspace="0em" rspace="0em">&#x2044;</mo><mi>d</mi><mi>t</mi></mrow></math>
---
# Overview
- *Definition:* controlling the rate of change which helps reduce overshooting
- *Effect:* increases stability, reducing the overshoot, and improving the [[transient response]].
$$
K_d \cdot \frac{de(t)}{dt} = K_d \cdot [e(t) - e(t - 1)] / dt
$$
# Variables
- $K_{d}$: derivative coefficient
- e(t): [[feedback error]]