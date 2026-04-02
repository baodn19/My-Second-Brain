---
modified: April 2nd 2026, 1:44:43 pm
---
- *Theorem:* $a,b\in \mathbb{Z}^+,a\equiv r$ (mod b) ([[division algorithm]])
	- r > 0 $\implies gcd(a,b)=gcd(b,r)$ ([[greatest common divisor]])
	- r = 0 $\implies gcd(a, b)=b$
- *Proof:* Since $a\equiv r$ (mod b), $\exists q\in \mathbb{Z}:a=bq+r$
	1. If d|b and d|r $\implies d|bq+r=a\implies$ d: a common [[divisor]] of b & a
	2. If d|a and d|b $\implies d|a-bq=r\implies$ d: a common divisor of b & r
	Thus, the [[set]] of common divisors of a & b = b & r
	$\implies$ gcd(a, b) = gcd(b, r)