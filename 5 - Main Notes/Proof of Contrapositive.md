---
created: January 27th 2026
categories:
  - "[[Concepts]]"
modified: January 29th 2026, 1:05:31 pm
tags:
  - mathematics
  - logic
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
- *Theorem:* $\forall n \in \mathbb{Z}, if 3\nmid(n+1)^2-1$, then $3\nmid n$
	- *Proof:* By contrapositive
			$\forall n \in \mathbb{Z}, if 3 |n \implies 3|(n+1)^2-1$
			Given $n \in \mathbb{Z}$. Assume $3|n \implies \exists k \in \mathbb{Z}: n=3k$
			$(n+1)^2 -1=(3k+1)^2-1=9k^2+6k=3(3k^2 +2k) \implies 3|((n+1)^2-1)$
- **