---
modified: April 11th 2026, 4:11:54 pm
---
- *Theorem:* $a,b\in \mathbb{Z}^+,a\equiv r$ (mod b) ([[division algorithm]])
	- r > 0 $\implies gcd(a,b)=gcd(b,r)$ ([[greatest common divisor]])
	- r = 0 $\implies gcd(a, b)=b$
	- *Proof:* Since $a\equiv r$ (mod b), $\exists q\in \mathbb{Z}:a=bq+r$
		1. If d|b and d|r $\implies d|bq+r=a\implies$ d: a common [[divisor]] of b & a
		2. If d|a and d|b $\implies d|a-bq=r\implies$ d: a common divisor of b & r
		Thus, the [[set]] of common divisors of a & b = b & r
		$\implies$ gcd(a, b) = gcd(b, r)
- *Theorem:* use table to find gcd. E.g: gcd(45, 12)

| 45    | 12  | 45 = 12(3) + 9  |
| ----- | --- | --------------- |
| 12    | 9   | 12 = 9(1) + 3   |
| 9     | 3   | 9 = 3(3) + 0    |
| **3** | 0   | gcd(45, 12) = 3 |
- Example: what is gcd(83, 17) and find s, t: $83s+17t=gcd(83,17)$

| 83    | 17  | 83 = 17.4 + 15  |
| ----- | --- | --------------- |
| 17    | 15  | 17 = 15.1 + 2   |
| 15    | 2   | 15 = 2.7 + 1    |
| 2     | 1   | 2 = 1.2 + 0     |
| **1** | 0   | gcd(83, 17) = 1 |
$\implies gcd(83,17)=1$ by the **Euclidean algorithm**
$1 = 15-7.2=15-7(17-15)=8.15-7.17=8(83-4.17)-7.17=(8)83+(-39)17$
$1=8.83+(-39)17\implies1\equiv 8.83$ mod(17) $\implies 8$ is the [[multiplicative inverse]] of 83 in mod 17