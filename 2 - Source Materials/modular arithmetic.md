---
categories:
  - "[[Concepts]]"
created: March 31st 2026
modified: April 2nd 2026, 12:45:55 pm
tags:
  - mathematics
---
- *Example:* In $\mathbb{Z}_{11}$ (mod 11):
	- 8 + 9 $\equiv$ 6 (mod 11) ([[division algorithm]])
	- 7.4 $\equiv$ 6 (mod 11)
- *Assume:* d > 1: m ~ n if m $\equiv$ n (mod d) (m, n $\in \mathbb{Z}$) ([[equivalence relation]])
	- d = 2:
	$[2]=[0]=\{m \in \mathbb{Z}$ s.t. m ~ 0} = $\{m \in \mathbb{Z}$ s.t. m $\equiv$ 0 (mod 2)} = {..., -2, 0, 2, ...}
	$[1] =$ $\{m \in \mathbb{Z}$ s.t. m $\equiv$ 1 (mod 2)} = {..., -1, 1, 3, ...}
- *Theorem:* a, b, m, n, d $\in \mathbb{Z},d>0$ 
	If a $\equiv$ m (mod d) & b $\equiv$ n (mod d)
	1. a + b $\equiv$ m + n (mod d)
	2. a.b $\equiv$ m.n (mod d)
	3. $a^c\equiv m^c$ (mod d)
	*Proof:* $\exists k\in \mathbb{Z}:a=dk+m$ & $\exists l\in \mathbb{Z}:b=dl+n$
	1- $a+b=dk+m+dl+n=d(k+l)+m+n\equiv$ m + n (mod d)
	2- $a.b=(dk+m)(dl+n)=m.n+d(kn+lm+kld)\equiv m.n$ (mod d)
- *Note:*
	- Use = when manipulating the same number
	- Use $\equiv$ when doing the division