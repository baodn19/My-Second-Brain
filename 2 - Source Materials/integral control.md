---
categories:
  - "[[Concepts]]"
  - "[[Formulas]]"
created: February 5th 2026
modified: April 20th 2026, 5:05:53 pm
tags:
  - control-system
formula: <math xmlns="http://www.w3.org/1998/Math/MathML"><mrow><msub><mi>K</mi><mi>i</mi></msub><mo>&#xb7;</mo><mrow><munderover><mo movablelimits="false">&#x2211;</mo><mn>0</mn><mi>t</mi></munderover></mrow><mi>e</mi><mo form="prefix" stretchy="false">(</mo><mi>t</mi><mo form="postfix" stretchy="false">)</mo><mspace width="0.1667em"></mspace><mi>d</mi><mi>t</mi></mrow></math>
---
# Overview
- *Definition:* take into account the amount of errors over time
- *Effect:* eliminating the steady-state error, but it may make the [[transient response]] worse
$$
K_i \cdot \int_{0}^{t} e(t) \cdot dt= K_i \cdot \sum_{0}^{t} e(t) \, dt
$$
# Variables
- $K_{i}$: integral coefficient
- e(t): [[feedback error]]