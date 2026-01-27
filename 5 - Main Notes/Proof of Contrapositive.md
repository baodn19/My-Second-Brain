---
created: January 27th 2026
categories:
  - "[[Concepts]]"
modified: January 27th 2026, 1:03:12 pm
tags:
  - mathematics
---
- *To show $P \longrightarrow Q$:* we show $\neg P \longrightarrow \neg Q$ ([[Contrapositive]])
- *Theorem:* $\forall n \in \mathbb{Z}$, if $4 \neq n^2$, then n is odd.
	- *Contrapositive:* $\forall n \in \mathbb{Z}$, if n is even $\implies 4 | n^2$  (include contrapositive in quiz)
	- *Proof:* Take $n \in \mathbb{Z}$; assume n is even $\implies \exists k \in \mathbb{Z}: n = 2k$
			Then $n^2 = (2k)^2 = 4k^2 \implies 4 | n^2$ (4 is a [[divisor]] $n^2$)
- *Theorem:* $\forall x, \forall y \in \mathbb{R}$, if $xy \in Irr$, then either x or y is in Irr
	- *Contrapositive:* $\forall x, \forall y \in \mathbb{R}$, if $x, y \in \mathbb{Q}$, then $xy \in \mathbb{Q}$
	- *Proof:* Take $x, y \in \mathbb{R}$; assume $x, y \in \mathbb{Q} \implies \exists p, q, r, s \in \mathbb{Z}$  such that $q \neq 0, s \neq 0$
			$x = \frac{p}{q}, y = \frac{r}{s}$
			Then $xy = \frac{p}{q} . \frac{r}{s} = \frac{pr}{qs}; pr \in \mathbb{Z}, qs \in \mathbb{Z}, qs \neq 0 \implies xy \in \mathbb{Q}$