---
modified: April 2nd 2026, 1:39:07 pm
---
- *Theorem:* There are infinitely many prime numbers
	- *Proof:* Assume, [[Proof of Contradiction]] , $\exists$ finitely many primes: $p_{1},\dots,p_{k}$. 
		Let n = $p_{1}.\dots .p_{k}+1$ . 
		By our assumption, n is not prime, $n>p,1\leq i\leq k$ and by [[fundamental theorem of arithmetic]], n has a prime [[divisor]]
		$\implies$ That prime divisor is one of the $p_{i}$'s, $1\leq i \leq k$
		$\implies p_{i}|n$ and $p_{i}|p_{1}.\dots .p_{i}.\dots .p_{k}$
		$\implies p_{i}|n-(p_{1}.\dots .p_{k})$
		$\implies p_{i}|1$  $\textreferencemark$ since $p_{i} > 1$
- [[Euclidean algorithm]]