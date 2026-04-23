---
categories:
  - "[[Concepts]]"
created: April 14th 2026
modified: April 23rd 2026, 3:25:38 pm
tags:
---
- *Definition:* if n pigeons fly into k pigeonholes, n > k, then some (at least one) pigeonhole contains more than one pigeon.
	- *Generalized:* if n pigeons fly into k pigeonholes and n > mk then at least one pigeonhole contains more than m pigeons **(at least m+1)**
- *Theorem:* A, B: finite sets. If $f:A\to B$ is a [[one-to-one (injective) function]] then $|A|\leq|B|$
	- *Proof:* [[Proof of Contradiction]]
		Assume: if |A| > |B| then any $f:A\to B$ isn't 1-1, i.e., $\exists x_{1}\neq x_{2}$ in A s.t. $f(x_{1})=f(x_{2})$
		(A: pigeons, B: pigeonholes)
- *Example:* 32 pairs of socks: 8 black, 4 brown, 10 white, 10 blue. How many socks do you need to grab from the drawer to ensure a matching pair?
	- Answer: 5 socks
- *Example:* Poker hand (5 cards) $\exists4$ suits
	By **pigeonhole principle**, in a poker hand $\exists$ at least 2 cards of the same suit