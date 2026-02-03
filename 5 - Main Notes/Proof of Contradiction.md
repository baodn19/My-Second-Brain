---
created: January 27th 2026
categories:
  - "[[Concepts]]"
modified: February 3rd 2026, 12:50:11 pm
tags:
  - mathematics
  - logic
---
- *To prove a theorem statement (T):* We assume T is false -> Prove the assumption is false -> T is true
- *Theorem:* In a group of 25 people, at least 3 were born in the same month (example of [[Pigeon Hole Principle]])
	- *Proof:* By contradiction
			Assume in a group of 25 people, no (3 or more) were born in the same month.
			i.e., for each month, there are (2 or less) people born in that month
			$\implies$ In a year, 12 x 2 = 24 or less people, but there are 25 people $\textreferencemark$ 
			$\implies$ Assumption is false $\implies$ Theorem is true
- *Theorem:* $\sqrt{2}$ is irrational
	- *Proof:* By contradiction
			Assume $\sqrt{2}$ is rational $\implies$ $\exists p, q \in \mathbb{Z}, q \neq 0$ such that $\sqrt{2} = \frac{p}{q}$ (we can also assume (q, p) = 1 - [[relatively prime]]) 
			$\implies$ $2 = \frac{p^2}{q^2}$ $\implies$ $2q^2 = p^2$ $\implies$ $p^2$ is even $\implies$ p is even
			(if p was odd $\implies$ $p^2$ odd $\iff$ $p^2$ even $\implies$ p is even - [[Contrapositive]])
			$\implies$ $\exists k \in \mathbb{Z}: p = 2k$. Plug in: $2q^2=p^2=(2k)^2=4k^2$
			$\implies q^2 = 2k^2$ 
			$\implies q^2$ is even $\implies$ q is even
			Hence, p and q are both even $\implies \exists l, k \in \mathbb{Z}: p=2l, q=2k$
			$\implies (p,q) \neq 1$ since 2 is a common [[divisor]] $\textreferencemark$ 
			$\implies$ Assumption is false $\implies \sqrt{2}$ is irrational
- *Theorem:* $\forall x, \forall y \in \mathbb{Z}, x^2 - 4y \neq 2$
	- *Proof:* By contradiction
			Assume: $\exists x, \exists y \in \mathbb{Z}: x^2 - 4y = 2$
			$x^2 =4y+2=2(2y+1) \implies x^2$ is even $\implies$ x is even $\implies \exists k \in \mathbb{Z}: x = 2k$
			Plug in x into the equation: 
			$(2k)^2 -4y = 2$
			$\iff 2k^2 -2y=1$
			$\iff 2(k^2 -y)=1 \neq 2$  $\textreferencemark$ 
			$\implies$ Assumption is false $\implies$ Theorem is true


