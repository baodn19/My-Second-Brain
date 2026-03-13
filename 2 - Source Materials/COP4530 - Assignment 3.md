---
created: 2026-03-13
categories:
  - "[[Class Lectures]]"
modified: March 13th 2026, 1:46:53 pm
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
3. R-4.13 
4. R-4.18