---
created: March 2nd 2026
categories:
  - "[[Concepts]]"
modified: March 4th 2026, 9:46:17 pm
tags:
  - probability
---
- *Definition (discrete random variable):* Models the count of discrete events occurring within a fixed interval (time or space) given a constant average rate.
- *Example:* Counting the number of network packets arriving at an edge device per millisecond.
- *Formula (without/ with time):*
$$
P(X=x)=\frac{\mu^x.e^{-\mu}}{x!}
$$
$$
P(X_{t}=x) = \frac{(\mu t)^x.e^{-\mu t}}{x!}
$$
- *[[Expected value]] & [[Variance]]:* $E[X_{t}]=V(X_{t})=\mu t$