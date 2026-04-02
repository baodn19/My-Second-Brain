---
created: March 3rd 2026
categories:
  - "[[Concepts]]"
modified: April 2nd 2026, 4:24:38 pm
tags:
  - probability
---
- *Definition:* represent the distribution of random, independent variables or state vectors to [[normal distribution]]
	- Simplified: the probability of an interval; applies to **continuous random variable**
$$
p(a\leq X\leq b)=\int_{a}^{b}f(x)  \, dx
$$
- *Mathematical form:*
	- $\sigma$: standard deviation
	- $\mu$: mean
	- $x$: state variable
$$
f(x)=\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^{2}}=\mathcal{N}(\mu,\sigma^{2})
$$
- *Properties:* 
	- Always non-negative
	- Total area under the curve equals 1
$$
\int_{-\infty}^{\infty}f(x)  \, dx=1
$$

