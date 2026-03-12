---
categories:
  - "[[Concepts]]"
created: March 12th 2026
modified: March 12th 2026, 1:22:45 pm
tags:
  - mathematics
---
- *Definition:* [[ordered list]] of numbers or other mathematical objects that follow a particular pattern
- *Notation:* $(a_{i})_{i}$
- *Prove:* $\forall n\in \mathbb{Z}^+,\sum_{i=1}^n \frac{1}{2^i}=1-\frac{1}{2^n}$ ([[principle of mathematical induction]])
		*Basis:* n = 1
			**want:** $\sum_{i=1}^1 \frac{1}{2^i}=1-\frac{1}{2}$
			$\frac{1}{2}=\frac{1}{2}$   $\Box$
		*Inductive Step:* Assume for k, show for k+1:
			Assume: $\sum_{i=1}^k \frac{1}{2^i}=1-\frac{1}{2^k}$
			**want:** $\sum_{i=1}^{k+1} \frac{1}{2^i}=1-\frac{1}{2^{k+1}}$	$$
			\sum_{i=1}^{k+1} \frac{1}{2^i}=\sum_{i=1}^{k} \frac{1}{2^i} +\frac{1}{2^{k+1}}=\left( 1-\frac{1}{2^k} \right)+\frac{1}{2^{k+1}}= 1-\frac{1}{2^k}+\frac{1}{2^k.2}=1-\frac{1}{2^k}\left( 1-\frac{1}{2} \right)
			$$$$
			=1-\frac{1}{2^k}. \frac{1}{2}=1- \frac{1}{2^{k+1}} \Box
			$$
			$\implies$ By induction, this is true $\forall n\in \mathbb{Z}^+$
			