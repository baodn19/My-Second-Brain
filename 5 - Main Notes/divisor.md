---
categories:
  - "[[Concepts]]"
created: January 27th 2026
modified: January 29th 2026, 1:44:50 pm
tags:
  - mathematics
---
- *Definition:* let $n, d \in \mathbb{Z}$, $d \neq 0$. We say "d divides n" if $\exists k \in \mathbb{Z}$ such that n=d.k
		   we denote this by d | n and call d a divisor of n
## Examples
- $a,b,c\in \mathbb{Z}$ if ab|c then a|c
	- *Proof:* Assume $ab|c \implies \exists k\in \mathbb{Z}:c=(ab)k\implies c=a(bk)\implies a|c$
- If $8\nmid x^2-1$, then x is even ([[Proof of Contrapositive]])
	- *Proof:* by [[Contrapositive]]
			Assume x: odd $\implies \exists k\in \mathbb{Z}:x=2k+1$
			$x^2-1=(2k+1)^2-1=4k^2+4k=4k(k+1)$ ([[consecutive integers]])
			without loss of generality, we assume k: even $\implies \exists m \in \mathbb{Z}:k=2m$
			$\implies4k(k+1)=4\cdot 2m(2m+1)=8m(2m+1)\implies8|x^2-1$
- If a<b and ab<3, then a =1 ($a,b\in \mathbb{Z}_{+}$) ([[Proof of Contradiction]])
	- *Proof:* by contradiction
			Assume a < b & $ab<3\cap a\neq1$
			We are given $a,b\in \mathbb{Z}_{+}\implies a>1\implies1<a<b$ & ab < 3
			The smallest possible values: a = 2, b = 3, but ab = 6 > 3 $\textreferencemark$
- $\forall a,b\in \mathbb{Z}$ if a|b $\implies \forall n\in \mathbb{N},a^n |b^n$
	- *Proof:* Assume: a|b $\implies \exists k\in \mathbb{Z}:ak=b\implies b^n=(ak)^n=a^nk^n\implies a^n |b^n$
