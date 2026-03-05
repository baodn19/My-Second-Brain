---
created: March 4th 2026
categories:
  - "[[Concepts]]"
modified: March 5th 2026, 4:09:31 pm
tags:
  - probability
---
- *Application (continuous random variable):* Models continuous data that clusters symmetrically about a mean ($\mu$) with spread defined by variance ($\sigma^2$).
- *Example:* The distribution of positioning errors (in millimeters) of a robotic end-effector executing a predefined trajectory.
- *Equation:*
$$
f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2} = \mathcal{N}(\mu, \sigma^2)
$$
	- $\sigma$: standard deviation
	- $\mu$: mean
	- $x$: state variable