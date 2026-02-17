---
created: 2026-02-10
modified: February 17th 2026, 1:30:49 pm
---
- *Subtraction:* A - B = $\{x|x \in A \wedge x\not\in B\}$ 
- *Prove:* $(A-B)-C=(A-C)-(B-C)$
		*want:* $(A-B)-C\subseteq(A-C)-(B-C)$
		Take $x \in(A-B)-C\implies x \in(A-B)$ and $x \not\in C$
		$x \in(A-B)\implies x \in A$ and $x \not\in B$
		show $(A-C)-(B-C)\Longleftrightarrow x \in(A-C)$ and $x \not\in (B-C)(=\neg(x \in B)\wedge(x \not\in C)=x \not\in B \vee x \in C)$   $\Box$
		*want*
- *Prove:* if $A \cup B \subseteq C \cup D, A\cap B=\emptyset, C \subseteq A,$ then $B \subseteq D$
		*want:* $B \subseteq D \Longleftrightarrow$ Take $x \in B$ and want: $x \in D$ 
		$x \in B$ and $B \subseteq A \cup B\subseteq C\cup D\implies x \in C$ or $x \in D$ (\*)
		$x \in B$ and $A \cap B=\emptyset\implies x \not\in A\implies x \not\in C (C\subseteq A)$
		From (\*), $x \in D$  $\Box$
