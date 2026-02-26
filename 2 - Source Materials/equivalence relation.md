---
created: February 24th 2026
categories:
  - "[[Concepts]]"
modified: February 26th 2026, 1:35:53 pm
tags:
  - mathematics
---
- *Definition:* a [[binary relation]] R on a set A is an **equivalence relation** if it is a [[reflexive relation]], [[symmetric relation]], and [[transitive relation]]
- *Notation:* if R is an **equivalence relation** and xRy $\implies$ x~y
- *3.2/5a:* On $\mathbb{R}, R:xRy$ iff $x-y\in \mathbb{Q}$
		$[0]=\mathbb{Q}$
- *3.2/11:* On $\mathbb{N}, S:xSy$ iff $3|(x,y)$. Prove: S isn't an equivalence relation
		S is not reflexive, since $2\in \mathbb{N}$ but $2 \not\mathrel{S} 2$ since $3\nmid4$
		S is symmetric: if $3|(x+y)\implies3|(y+x)$
		S is not transitive: $\exists x,y,z \in \mathbb{N},xSy \cap ySz$ but $x\not\mathrel{S}z$
						$x+y=3k, k\in \mathbb{N}$
						$y+z=3l,l \in \mathbb{N}$
						$x+z=3k +3l-2y,\exists y\in \mathbb{N}$ s.t. $3\nmid(x+z)$
- *Ex1:* For $x, y\in \mathbb{R}, xRy$ iff $x-y\in \mathbb{Z}$
		$x \in \mathbb{R},[x]=\{y\in \mathbb{R}|yRx$ or $xRy\}=\{x+k|k\in \mathbb{Z}\}$
		Take $y\in \mathbb{R}:yRx$ iff $y-x \in \mathbb{Z}$
					iff $\exists k\in \mathbb{Z}:y-x=k$
					iff $\exists k\in \mathbb{Z}:y=x+k$
		