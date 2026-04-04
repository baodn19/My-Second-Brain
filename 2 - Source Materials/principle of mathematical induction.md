---
created: March 12th 2026
categories:
  - "[[Concepts]]"
modified: April 3rd 2026, 11:10:48 pm
tags:
  - mathematical-induction
---
- *Theorem:* S(n): a [[predicate]] with domain $\mathbb{Z}^+$ (countable variables). If:
	1. *Basis case:* S(1) is true
	2. *Inductive step:* $\forall k\in \mathbb{Z}^+,S(k)\implies S(k+1)$ is true
	3. Then: S(n) is true $\forall n\in \mathbb{Z}^+$
- *Example:*
	- [[Tower of Hanoi]]
	- Domino: If you know over the $1^{st}$ domino (base case) (n=1)
				a falling domino knocks down the next one (inductive step) ($k\implies k+1$)
				$\implies$ they all fall over (true $\forall n\in \mathbb{Z}^+$)
	- [[sequence]]
- [[strong induction]]
- *Prove:* For $n \geq 4,n^2 \leq 2^n$
	*Basis:* n = 4: $4^2 \leq 2^4$   $\Box$
	*Inductive Step:* For some $k \geq 4$, assume: $k^2 \leq 2^k$
		**want:** $(k+1)^2 \leq 2^{k+1}$
		$k \geq 4 \iff k^2 \geq 4k$
		**want:** $4k \leq 2^k$
		we know: $k^2 \leq 2^k \implies 4k \leq k^2 \leq 2^k$   
		$$
		(k+1)^2=k^2+2k+1\leq 2^k + 2+ 1\leq 2^k
+ 2k+2k	\leq 2^k + 2^k = 2^{k+1}	\Box$$
	Thus, by induction, S(n) is true $\forall n\geq 4$
- *Prove:* $\forall n\in \mathbb{Z}^+,6|7^n-1$ ([[divisor]]) (i.e., $\forall n\in \mathbb{Z}^+,\exists d\in \mathbb{Z}$ s.t. $7^n-1=6d$)
	*Basis:* n = 1: 6 | 7 - 1 = 6   $\Box$
	*Inductive Step:* Assume for some $k\in \mathbb{Z}^+,6|7^k-1$ 
		**want:** $6|k^{k+1}-1$
		$6|7^k-1\implies \exists d\in \mathbb{Z}:6d=7^k-1\implies6d+1=7^k$$$
		7^{k+1}-1=(7^k.7)-1=((6d+1).7)-1=42d+7-1=42d+6=6(7d+1); (7d+1)\in \mathbb{Z}
		$$
		$\implies6|7^{k+1}-1$
		Thus, by induction, theorem is true $\forall n\in \mathbb{Z}^+$
- *Prove:* A: a finite set. $|\mathscr{P}(A)|=2^{|A|}$ ([[power set]])
	*Basis:* If $A = \emptyset\implies \mathscr{P}(A)=\{\emptyset\}\implies|\mathscr{P}(A)|=1=2^0=2^{|A|}$
	*Inductive step:* Assume: for some $k \in \mathbb{N}$, if A is a set: |A| = k then $|\mathscr{P}(A)|=2^{k}$
				Let B be a set: |B| = k + 1. **want:** $|\mathscr{P}(B)|=2^{|B|}=2^{k+1}$
				Take $y\in B$
				Consider: S = B - {y} $\implies|S|=k\implies$ The statement is true for S by our assumption $\implies |\mathscr{P}(S)|=2^{|S|}=2^{k}$
				Now, every subset of B either:
				i) doesn't contain y $\implies$ The subset of B is a subset of S
				ii) contain y $\implies$ The subset of B = (a subset of S) $\cup$ {y}
				Since the $|\mathscr{P}(S)|$ of each type has the same number of elements
				$\implies|\mathscr{P}(B)|=2\implies|\mathscr{P}(S)|=2.2^k=2^{k+1}=2^{|B|}$
	Thus, by induction, for all finite sets A, $|\mathscr{P}(A)|=2^{|A|}$   $\Box$
- *Prove (6f):* for $\forall n \in \mathbb{Z}^{+}:$
$$
\sum ^{n}_{i=1} (2i-1)^3=n^2(2n^2 -1) (*)
$$
	*Basis:* n = 1: 
		LHS: $\sum ^{1}_{i=1} (2-1)^3=(2-1)^3=1$
		RHS: $1^2(2.1^2 -1)=1$
		$\implies$ LHS = RHS   $\Box$
	*Inductive step:* Assume $(*)$ for some $k \in \mathbb{Z}^{+}$, show $(*)$ for k+1. Assume:
$$
\sum ^{k}_{i=1} (2i-1)^3=k^2(2k^2 -1) 
$$
		*Want:* 
$$
\sum ^{k+1}_{i=1} (2i-1)^3=(k+1)^2[2(k+1)^2 -1]
$$
		LHS: $\sum ^{k}_{i=1} (2i-1)^3+[2(k+1)-1]^3=k^2(2k^3-1)+(2k+1)^3=2k^4-k^2+8k^3+12k^2+6k+1=2k^4+8k^3+11k^2+6k+1$
		RHS: $(k^2+2k+1)(2k^2+4k+1)=2k^4+8k^3+11k^2+6k+1$
		$\implies$ LHS = RHS  $\Box$
	So, by induction $(*)$ is true $\forall n \in \mathbb{Z}^{+}$
- *Prove (6h):* 
$$
\frac{1}{2!}+\frac{2}{3!}+\dots+\frac{n}{(n+1)!}=1-\frac{1}{(n+1)!}(*);\forall n \in \mathbb{Z}_{+}
$$
	*Basis:* n = 1: 
		LHS: $\frac{1}{2!}=\frac{1}{2}$
		RHS: $1-\frac{1}{2!}=1-\frac{1}{2}=\frac{1}{2}$
		$\implies$ LHS = RHS   $\Box$
	*Inductive Step:* assume $(*)$ for some $k \in \mathbb{Z}_{+},$ show $(*)$ for k + 1
		*Want:* 
	$$
	\frac{1}{2!}+\dots+\frac{k}{(k+1)!}+\frac{k+1}{(k+2)!}=1-\frac{1}{(k+2)!}
	$$
		LHS: $\left( 1-\frac{1}{(k+1)!} \right)+ \frac{k+1}{(k+2)!}=\frac{(k+2)[(k+1)!-1]}{(k+2)(k+1)!}+ \frac{k+1}{(k+2)!}=\frac{(k+2)!-(k+2)+k+1}{(k+2)!}=\frac{(k+2)!-1}{(k+2)!}$ 
		RHS: $\frac{(k+2)!-1}{(k+2)!}$
		$\implies$ LHS = RHS   $\Box$
	So, by induction $(*)$ is true $\forall n \in \mathbb{Z}_{+}$
- *Prove (7j):* $4^{n+4}>(n+4)^4(*),\forall n\in \mathbb{Z}_{+}$
	*Basis:* n = 1:
		LHS: $4^5=1024$
		RHS: $5^4=625$
		$\implies$ LHS > RHS   $\Box$
	*Inductive step:* Assume $(*)$ for some $k\in \mathbb{Z}_{+}$, show $(*)$ for k + 1
		*Want:* $4^{k+5}>(k+5)^4$
		LHS: $4^{k+4}.4>(k+4)^4.4=\left[ (k+4).4^{\frac{1}{4}} \right]^4=(1.41k+5.64)^4>(k+5)^4$
		$\implies$ LHS > RHS
	So, by induction $(*)$ is true $\forall n \in \mathbb{Z}_{+}$
- *Prove (7m):* $\frac{n^3}{3}+\frac{n^5}{5}+\frac{7n}{15}$ is an integer $\forall n \in \mathbb{Z}_{+}$
	*Basis:* n = 1: $\frac{1}{3}+\frac{1}{5}+\frac{7}{15}=1$  $\Box$
	*Inductive step:* Assume for some $k\in \mathbb{Z}_{+},$ show for k + 1
	$$f(k) = \frac{3k^5 + 5k^3 + 7k}{15} = A\iff3k^5 + 5k^3 + 7k = 15A$$
		*want:* Is $\frac{(k+1)^3}{3}+\frac{(k+1)^5}{5}+\frac{7(k+1)}{15}$ an integer?
		$\frac{(3k^5 + 5k^3 + 7k) + 15k^4 + 30k^3 + 45k^2 + 30k + 15}{15}=\frac{15(A + k^4 + 2k^3 + 3k^2 + 2k + 1)}{15}=15(A + k^4 + 2k^3 + 3k^2 + 2k + 1) \in \mathbb{Z}_{+}$
		
	So, by induction $(*)$ is true $\forall n \in \mathbb{Z}_{+}$
	