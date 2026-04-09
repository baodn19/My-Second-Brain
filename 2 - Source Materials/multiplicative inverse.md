---
created: April 9th 2026
modified: April 9th 2026, 1:31:58 pm
categories:
  - "[[Concepts]]"
tags:
---
- *Definition:*  s is the **multiplicative inverse** of a mod b if $sa\equiv1$ (mod b)
- *Remark:* x has an [[inverse]] in mod n $\iff$ gcd(x, n) = 1 ([[modular arithmetic]])
	- Example: 6 doesn't have an inverse in mod 4:
		$6x\equiv 1$ (mod 4) $\implies x\equiv \frac{1}{6}$ (mod 4) $\implies x=\frac{1+4k}{6} \implies 6x=1+4k$    $\textreferencemark$
	- *Special case:* $gcd(a,b)=1 \implies \exists s,t\in \mathbb{Z}$ s.t. $sa+tb=1\implies sa=-tb +1$ ([[greatest common divisor]])
				$\implies sa\equiv1$ (mod b) $\implies$ s is the **multiplicative inverse** of a mod b
	- Example: Find the multiplicative inverse of 7 (mod 100)
		$gcd(7, 100)=1\implies \exists$ an inverse
([[Euclidean algorithm]])

| 100   | 7   | 100 = 7(14) + 2 |
| ----- | --- | --------------- |
| 7     | 2   | 7 = 2(3) + 1    |
| 2     | 1   | 2 = 1(2) + 0    |
| **1** | 0   | gcd(100, 7) = 1 |
		 $1=7-2.3=7-(100-7.14).3=(43)7+(-3)100\implies1\equiv43.7$ (mod 100)
		 $\implies$ 43 is the multiplicative inverse of 7 in mod 100