---
created: March 12th 2026
categories:
  - "[[Concepts]]"
modified: March 15th 2026, 9:41:47 pm
tags:
  - mathematical-induction
---
- *Theorem:* S(n): a [[predicate]] with domain $\mathbb{Z}^+$ (countable variables). If:
	1. *Basis case:* S(1) is true
	2. *Inductive step:* $\forall k\in \mathbb{Z}^+,S(k)\implies S(k+1)$ is true
	3. Then: S(n) is true $\forall n\in \mathbb{Z}^+$
- *Example:*
	- [[Tower of Hanoi]]
	- Domino: If you know over the $1^{st}$ domino (base case) (n=1)
				a falling domino knocks down the next one (inductive step) ($k\implies k+1$)
				$\implies$ they all fall over (true $\forall n\in \mathbb{Z}^+$)
	- [[sequence]]
- [[strong induction]]
- *Prove:* For $n \geq 4,n^2 \leq 2^n$
	*Basis:* n = 4: $4^2 \leq 2^4$   $\Box$
	*Inductive Step:* For some $k \geq 4$, assume: $k^2 \leq 2^k$
		**want:** $(k+1)^2 \leq 2^{k+1}$
		$k \geq 4 \iff k^2 \geq 4k$
		**want:** $4k \leq 2^k$
		we know: $k^2 \leq 2^k \implies 4k \leq k^2 \leq 2^k$   
		$$
		(k+1)^2=k^2+2k+1\leq 2^k + 2+ 1\leq 2^k
+ 2k+2k	\leq 2^k + 2^k = 2^{k+1}	\Box$$
	Thus, by induction, S(n) is true $\forall n\geq 4$
- *Prove:* $\forall n\in \mathbb{Z}^+,6|7^n-1$ ([[divisor]]) (i.e., $\forall n\in \mathbb{Z}^+,\exists d\in \mathbb{Z}$ s.t. $7^n-1=6d$)
	*Basis:* n = 1: 6 | 7 - 1 = 6   $\Box$
	*Inductive Step:* Assume for some $k\in \mathbb{Z}^+,6|7^k-1$ 
		**want:** $6|k^{k+1}-1$
		$6|7^k-1\implies \exists d\in \mathbb{Z}:6d=7^k-1\implies6d+1=7^k$$$
		7^{k+1}-1=(7^k.7)-1=((6d+1).7)-1=42d+7-1=42d+6=6(7d+1); (7d+1)\in \mathbb{Z}
		$$
		$\implies6|7^{k+1}-1$
		Thus, by induction, theorem is true $\forall n\in \mathbb{Z}^+$
	