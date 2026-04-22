---
created: 2026-04-02
modified: April 22nd 2026, 1:42:31 pm
---
- *Definition:* $\forall n\in \mathbb{Z}^+,n>1$ factors **uniquely** as a product of primes
$\implies \forall n\in \mathbb{Z}^+, n>1$ has a prime [[divisor]]
- *Theorem:* $m,n\in \mathbb{Z};m,n>1:$ where $p_{i}$'s are primes (if $p_{i}$ isn't a divisor of m or n, set $a_{i}=0$ or $b_{i}=0$)
$$
m=p_{1}^{a_{1}}.p_{2}^{a_{2}}.\dots .p_{k}^{a_{k}}
$$
$$
n=p_{1}^{b_{1}}.p_{2}^{b_{2}.}\dots .p_{k}^{b_{k}}
$$
then:
1. gcd(m, n) = $p_{1}^{c_{1}}.p_{2}^{c_{2}.}\dots .p_{k}^{c_{k}}$ where $c_{i}=min\{a_{i},b_{i}\}$ ([[greatest common divisor]])
2. lcd(m, n) = $p_{1}^{d_{1}}.p_{2}^{d_{2}.}\dots .p_{k}^{d_{k}}$ where $d_{i}=max\{a_{i},b_{i}\}$ ([[least common multiple]])
3. gcd(m ,n) . lcm(m, n) = m.n
- If n is a [[composite number]] $\implies n=dk,2\leq d\leq n-1$ (n > 1)
- *Theorem:* Suppose $n\in \mathbb{Z}^+, n>1$. If n is composite, then d|n for some $2\leq d\leq \sqrt{ n }$
	- *Proof:* by [[Proof of Contradiction]]
		Suppose n is composite, $n\in \mathbb{Z}^+,n>1\implies \exists k,l\in \mathbb{Z}^+:k,l\geq 2$ and $n=kl$
		If both k & l > $\sqrt{ n}$, then $n=kl>\sqrt{ n }\sqrt{ n }=n$   $\textreferencemark$
		$\implies$ At least one of k & l $\leq \sqrt{ n }$
		$\implies \exists$ a divisor of n, say k, $2\leq k\leq \sqrt{ n }$  $\Box$
