---
created: January 29th 2026
categories:
  - "[[Concepts]]"
modified: January 29th 2026, 1:17:27 pm
tags:
  - mathematics
  - logic
---
- *Theorem:* the product of an odd and an even integer is even
	- *Proof:* give x, y; assume x: odd, y: even
			$\implies \exists k, l \in \mathbb{Z}: x=2k+1, y=2l$
			$\implies xy=(2k+1)(2l)=2(2kl+l)$ 
## True/ False? - Domain: $\mathbb{R}$
- $\forall x \forall y\exists z,\left( z=\frac{x-y}{3} \right)$
	- x, y: given
	- Take $\left( z=\frac{x-y}{3} \right)$ (**TRUE**)
- $\exists x \exists y\exists z, (x^2 + y^2 = z^2)$
	- In $\mathbb{Z} - \{0\}$
	- x = 3, y = 4, z = 5 (**TRUE**)
- $\forall x \exists y \in \mathbb{R}, (y^2 = x)$
	- if $x < 0 \implies \nexists y: y^2=x$ (**FALSE**)
- $\exists x \exists y,(x^2=y^2\cap x\neq y)$
	- In $\mathbb{Z}$, take x & y = -x (**TRUE**)
- $\forall x\forall y \in \mathbb{R},(x^2\neq y^2\cup|x|=|y|)$
	- Given $x, y \in \mathbb{R}$
	- $\implies |x|=|y|\implies TRUE$
	- or $|x|\neq|y|\implies y\neq\pm x \implies x^2\neq(\pm x^2)=x^2$ (**TRUE**)