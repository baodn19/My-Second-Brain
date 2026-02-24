---
created: February 19th 2026
categories:
  - "[[Concepts]]"
modified: February 24th 2026, 1:17:49 pm
tags:
  - mathematics
---
- *Definition:* a binary relation R from [[set]] A to set B is a [[subset]] of $A\times B$
			if A = B, we say R is a relation on A
- *Notation:* if $(x,y)\in R$, we write xRy
- *Example:* $R = \{(x,y)\in \mathbb{R}^2|y=x^2\}\implies R=\{(0,0),(1,1),(2,4),(3,9),\dots\}$
- *Example:* A = {USF students}, B = {USF classes}
			$R=\{(x,y)\in A\times B|$ x is enrolled in y}
- *vs [[function]]:* relation is more general than function
- *Properties:*
	-  A={USF students}, $R=\{(x,y) \in A\times A|$x is enrolled in the same class as y}:
		- [[reflexive relation]] since xRx or $(x,x)\in R$
		- [[symmetric relation]] since if xRy $\implies$ yRx
		- not [[transitive relation]] since xRy and yRz but x and z many not be in the same class
	-  $R=\{(x,y)\in \mathbb{R}^2|x<y\}$:
		- not reflexive relation since x < x cannot happen
		- not symmetric relation since if $xRy \implies x < y\implies y\not\mathrel{R}x$
		- transitive relation since if xRy and yRz $\implies xRz$
	- $R = \{(x,y)\in \mathbb{R}^2| |y-x| \leq 1\}$:
		- reflexive relation since $\forall x \in R, |x-x|=0\leq 1\implies(x,x)\in R$
		- symmetric relation since if xRy $\implies|y-x|\leq 1\implies|x-y| \leq 1\implies yRx$
		- not transitive relation since $-1R0$ and 0R1 but $-1\not\mathrel{R} 1$