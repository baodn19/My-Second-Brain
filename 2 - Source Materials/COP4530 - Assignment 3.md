---
created: 2026-03-13
categories:
  - "[[Class Lectures]]"
modified: March 23rd 2026, 11:37:50 pm
class:
  - "[[COP4530]]"
tags:
  - algorithm
---
1. R-4.7 
- For algorithm A to be better than algorithm B, A must have less operations than B for $n \geq n_{0}$. For algorithm A, we can assume the logarithm has base-2 which is standard practice. We have the inequality below:
$$
8n\log_{2} n<2n^2 \iff4\log_{2} n<n
$$
- We try different values of $n$:
	- $n=16$: $4 \log_2(16) = 4(4) = 16$ (invalid)
	- $n = 17$: $4 \log_2(17) \approx 4(4.087) \approx 16.35$ (valid since 16.35 < 17)
$\implies$ At $n_{0}=17$, A is better than B for $n \geq n_{0}$.

2. R-4.8 
- For algorithm A to be better than algorithm B, A must have less operations than B for $n \geq n_{0}$. We have the inequality below:
$$
40n^2< 2n^3 \iff20<n
$$
$\implies$ At $n_{0}=21$, A is better than B for $n \geq n_{0}$.

3. R-4.13 
- Functions ordered from lowest to highest asymptotic growth rate:
	1. $O(1)$: $2^{10}$
	2. $O(n)$: $2^{\log n},3n+100\log n, 4n$
	3. $O(n\log n)$: $n\log n, 4n\log n+2n$
	4. $O(n^2)$: $n^2+10n$
	5. $O(n^3)$: $n^3$
	6. $O(2^n)$: $2^{n}$

4. R-4.18
- The `Ex3` function in Code Fragment 4.6. has a running time of $O(n^2)$
- Explanation:
	1. The outer loop runs from i = 0 to i = n - 1 $\implies$ The outer loop runs n times
	2. The inner loop's iteration depends on i. The total number of iterations from the inner loop is as below:
$$
0+1+2+\dots+(n-1)=\sum^{n-1}_{k}k=\frac{n(n-1)}{2}=\frac{n^2}{2} - \frac{n}{2}
$$
	3. The highest-order term is $n^2\implies$ Time complexity: $O(n^2)$ 