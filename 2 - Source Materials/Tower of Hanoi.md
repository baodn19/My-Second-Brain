---
created: March 12th 2026
categories:
  - "[[Concepts]]"
modified: March 12th 2026, 12:57:45 pm
tags:
  - mathematical-induction
---
- *Goal:* move washers of different sizes from one stick to another
- *Rules:*
	1. Only move 1 washer at a time
	2. Cannot place a bigger washer on top of a smaller washer
- *Theorem:* $\forall n\in \mathbb{N}$, the tower of [[Hanoi]] with n washers has a solution
- *Proof:* For n=1, this is obvious
		Let $n \geq 1$, suppose: the tower of Hanoi with n washers has a solution
		![[Tower of Hanoi proof.png]]
		$\implies$ There is a solution for (n+1)
		$\implies \forall n \in \mathbb{N}$, tower of Hanoi has a solution ([[principle of mathematical induction]])