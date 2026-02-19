---
categories:
  - "[[Concepts]]"
created: February 19th 2026
modified: February 19th 2026, 1:30:53 pm
tags:
  - mathematics
---
- *Definition:* $f: \mathbb{N}\to \mathbb{N},f(n)=n^2$
- *Prove:* f is an [[one-to-one (injective) function]]
		Take $n_{1}, n_{2} \in \mathbb{N}$, assume $f(n_{1})=f(n_{2})$, *want:* $n_{1}=n_{2}$
		$\implies n_{1}^2=n_{2}^2\implies n_{1}=\pm n_{2}$ but $n_{1}, n_{2} \in \mathbb{N}\implies n_{1}=n_{2}$  $\Box$
- *Prove:* f isn't an [[onto (surjective) function]]
		$7 \in \mathbb{N},$ but $\sqrt{ 7 }\not\in \mathbb{N}\implies7 \not\in$ range f
- *Prove:* $\rho:\mathbb{Z}\to \mathbb{N}, \rho(n)=n^2$ isn't 1-1
		$\rho(2)=4=\rho(-2)$  
- *Prove:* $h:\mathbb{R}^+ \to \mathbb{R}^+: h(x) = x^2$ is 1-1
		Take $x_{1}, x_{2}\in \mathbb{R}^+$. Assume $h(x_{1}) = h(x_{2}),$ *want:* $x_{1}=x_{2}$
		$\implies x_{1}^2=x_{2}^2\implies x_{1}=\pm x_{2},$ but $x_{1},x_{2}\in \mathbb{R}^+\implies x_{1}=x_{2}$
- *Prove:* $h$ is into since $\forall y\in \mathbb{R}^+,\exists x \in R^+,x=\sqrt{ y }\implies h(\sqrt{ y })=y\implies y\in$ range h  $\Box$
