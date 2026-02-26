---
created: February 17th 2026
categories:
  - "[[Concepts]]"
modified: February 26th 2026, 2:36:48 pm
tags:
  - mathematics
---
- *Definition:* a rule that assigns to each element of some [[set]] A **exactly one element** of some [[set]] B
- *Formal definition:* a "function" from A to B is a [[subset]] $f \subseteq A \times B$ such that $\forall x \in A$, there is exactly one $y \in B$ with $(x,y)\in f$. This unique is y is denoted as f(x)
- *Notation:* $f: A\to B$
	- A: domain
	- B: target
	- f(A): [[function range]]
- *Special:*
	- [[natural number function]]
	- [[power set function]]
	- [[floor function]]
	- [[square function]]
- *Properties:* A, B: finite set. $\exists|B|^{|A|}$ functions from A to B
- *4.1/4c:* Assume domain and range are the largest possible [[subset]] of $\mathbb{R}$. What is the domain and range of $f(x)=\frac{1}{\sqrt{ x+\pi }}$
		*Domain:* $\{x \in \mathbb{R}|x>-\pi\}=(-\pi, \infty)$
		*Range:* $\mathbb{R}_{+}=(0,+\infty)$
- *4.1/6a:* Show that the following [[binary relation]] isn't a function on $\mathbb{R}$. $\{(x,y)\in \mathbb{R}\times \mathbb{R}|x^2=y^2\}$
		If it was a function, $\{(x,f(x))\in \mathbb{R}\times \mathbb{R}\}$
		$f: \mathbb{R} \to \mathbb{R}$
		 $x$