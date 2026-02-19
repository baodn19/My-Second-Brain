---
categories:
  - "[[Concepts]]"
created: February 19th 2026
modified: February 19th 2026, 1:07:35 pm
tags:
  - mathematics
---
- *Definition:* k: $\mathscr{P}(\{1,2,3\})\to\mathscr{P}(\{1,2,3\})$
			$k(A) =A \cup\{1\}$
	- A: element of [[power set]]
- *Prove:* k isn't an [[one-to-one (injective) function]]
		k({2}) = {1, 2}
		k({1, 2}) = {1, 2}
		$\{2\} \neq\{1,2\}$, but both have the same k  $\textreferencemark$
- *Prove:* k isn't an [[onto (surjective) function]]
		since $\emptyset \not\in$ range of k
		$\nexists A$ in the domain s.t. $k(A)=A\cup\{1\}=\emptyset$  $\Box$