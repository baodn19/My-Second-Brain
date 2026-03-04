---
created: March 3rd 2026
categories:
  - "[[Concepts]]"
modified: March 4th 2026, 8:17:20 am
tags:
  - probability
---
- *Definition:* the [[probability]] that a random variable takes a value less than or equal to a specific value $x$; applies to both **discrete & continuous random variables**
$$
F(x)=p(X\leq x)
$$
- *Relationship:*
	- [[probability mass function (pmf)]]:
$$F(x) = \sum_{t \le x} P(X = t)
$$
	- [[probability density function (pdf)]]:
$$F(x) = \int_{-\infty}^{x} f(t) dt$$
- *Properties:*
	- *Non-decreasing function*: As $x$ increases, $F(x)$ either increases or remains constant.
	- Bounded between 0 and 1: $0 \le F(x) \le 1$
- *[[box plot]]:*
	- $Q_{3}$ quartile: $p(X\leq Q_{3})=0.75$
	- $Q_{1}$ quartile: $p(X\leq Q_{1})=0.25$

