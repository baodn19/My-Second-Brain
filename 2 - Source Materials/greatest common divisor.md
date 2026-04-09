---
created: 2026-04-02
modified: April 9th 2026, 1:29:27 pm
---
- *Definition:* $m,n\in \mathbb{Z},m\neq 0,n\neq 0$; the largest positive integer dividing both m and n
- *Notation:* gcd(m, n)
- *Theorem:* $a,b\in \mathbb{Z}^+\implies \exists s,t\in \mathbb{Z}$ s.t. gcd(a, b) = sa + tb
	- *Method:* work the steps of the [[Euclidean algorithm]] backwards, starting where gcd is a remainder
	- Example: $gcd(45, 12) = 3 = 12 - 9(1) = 12 - [45-12(3)] =12-45+36=(-1)45+(4)12$ 
