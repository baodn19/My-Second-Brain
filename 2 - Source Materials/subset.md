---
created: February 3rd 2026
categories:
  - "[[Concepts]]"
modified: February 12th 2026, 1:40:16 pm
tags:
  - logic
  - set-theory
  - mathematics
---
- *Definition:* $A\subseteq B \Longleftrightarrow \forall x, x \in A \implies x \in B$
			$A=B\Longleftrightarrow(A\subseteq B)\wedge(B\subseteq A)$
- *Notation:* $A \subseteq B$: every element of A is also an element of B
- *Example:*
	- $\mathbb{N} \subseteq \mathbb{Z} \subseteq \mathbb{Q} \subseteq \mathbb{R}$
	- $\emptyset \subseteq$ any set
	- $\forall$ set $S, S \subseteq S$
- *Prove:* if $A\subseteq B,B \subseteq C, C \subseteq A$, then $(A=B) \wedge (B=C)$
		Take $x \in B\implies x \in C$ since $B\subseteq C\implies x \in A$ since $C \subseteq A \Box$ 
- *Prove:* $A\subseteq B\Longleftrightarrow A-B=\emptyset$
		Assume $(A\subseteq B)\wedge(A-B \neq \emptyset) \implies \exists x \in A-B\implies x \in A \wedge x \not\in B$
		Since $A \subseteq B\implies \forall x:x \in A \implies x \in B$ $\textreferencemark$ ([[Proof of Contradiction]])
		$\implies A\subseteq B\implies A-B=\emptyset$
		Assume $A\nsubseteq B\implies \neg(A\subseteq B)=\neg(\forall x,x \in A \implies x \in B)=\exists x:x \in A \wedge x\not\in B$
		$\implies x \in A-B\implies A-B\neq \emptyset$  $\Box$ ([[Proof of Contrapositive]])
- *Prove:* If $C\subseteq A$ and $D \subseteq B$, then $(C\cup D)\subseteq (A\cup B)$
		Assume $C\subseteq A$ and $D \subseteq B$
		Take $x \in C\cup D\implies x \in C$ or $x \in D$
		Since $C\subseteq A\implies x \in A$
		Since $D\subseteq B \implies x \in B$
		$\implies x \in A \cup B$  $\Box$ 