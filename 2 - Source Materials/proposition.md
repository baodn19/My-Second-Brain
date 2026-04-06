---
created: February 3rd 2026
categories:
  - "[[Concepts]]"
modified: April 6th 2026, 10:30:04 am
tags:
  - mathematics
  - logic
---
# Overview
- *Logic:* $\neg P \vee Q$

## To prove $P \to Q$
- **NEVER:** start with assume Q
- *[[direct proof]]*: Assume P and want to show Q
- *[[Proof of Contradiction]]*: Assume $P\cap\neg Q$
- *[[Proof of Contrapositive]]*: Assume $\neg P$ then show $\neg Q$

## Example
- *Theorem:* If $x \in \mathbb{Q}$ and $y\in Irr\implies x+y\in Irr$
	- *Contradiction:* Assume $(x \in \mathbb{Q}, y \not\in \mathbb{Q})\cap(x+y \not\in \mathbb{Q})$
					$\exists p,q \in \mathbb{Z}, q \neq 0: x = \frac{p}{q}$
					$x+y\in \mathbb{Q}\implies \exists r,s \in\mathbb{Z},s\neq0:x+y=\frac{r}{s}$
					$y=(x+y)-x=\frac{r}{s} - \frac{p}{q} = \frac{rq-sp}{sq};sq\neq0,rq-sp \in \mathbb{Z}, sq \in \mathbb{Z}$
					$\implies y\in \mathbb{Q} \textreferencemark$
	-  *Contrapositive:* Assume $x+y \in \mathbb{Q}$, want: $x \not\in \mathbb{Q}$ or $y \in \mathbb{Q}$
					$\exists k,l \in \mathbb{Z}, l \neq 0: x+y = \frac{k}{l}$
					i) If $x \not\in \mathbb{Q} \implies$ done
					ii) If $x \in \mathbb{Q} \implies$ want: $y \in \mathbb{Q}\implies \exists a,b \in \mathbb{Z}, b\neq 0: x=\frac{a}{b}$
					$y = (x+y) - x=\frac{k}{l}-\frac{a}{b}=\frac{kb-la}{lb}, lb\neq 0$
					$\implies y \in \mathbb{Q}$  $\square$ 
					