---
created: April 14th 2026
categories:
  - "[[Concepts]]"
modified: April 14th 2026, 1:38:12 pm
tags:
  - mathematics
---
- *Definition:* for:
	- 2 finite sets A, B: $|A\cup B|=|A|+|B|-|A\cap B|=|A\backslash B|+|B\backslash A|+|A\cap B|$
	- 3 finite sets A, B, C: $|A\cup B\cup C|=|A|+|B|+|C|-|A\cap B|-|B\cap C|-|A\cap C|+|A\cap B\cap C|$
- *Example:* How many integers $1\leq n\leq100$ are divisible by 2, 3, **or** 5?
	A: set of integers $1\leq n\leq100$ divisible by 2
		$|A|=\frac{100}{2}=50$
	B: set of integers $1\leq n\leq100$ divisible by 3 ([[floor function]])
		$|B|=\left\lfloor \frac{100}{3} \right\rfloor=33$
	C: set of integers $1\leq n\leq100$ divisible by 5
		$|C|=\frac{100}{5}=20$
	$A\cap B$: set of integers $1\leq n\leq100$ divisible by 2 and 3
		$|A\cap B|=\left\lfloor \frac{100}{6} \right\rfloor=16$
	$B\cap C$: set of integers $1\leq n\leq100$ divisible by 3 and 5
		$|B \cap C|=\left\lfloor \frac{100}{15} \right\rfloor=6$
	$A \cap C$: set of integers $1\leq n\leq100$ divisible by 2 and 5
		$|A\cap C|=\frac{100}{10}=10$
	By the **inclusion-exclusion principle**, $|A\cup B\cup C|=|A|+|B|+|C|-|A\cap B|-|B\cap C|-|A\cap C|+|A\cap B\cap C|=50+33+20-16-6-10+3=74$
- *Example:* How many strings of length 8 over {0, 1, 2} either start with 0 or end with 12?
	In total, $3^8$ strings of length 8 over {0, 1, 2}
	A: set of strings starting with 0
		$|A|=3^7$
	B: set of strings ending with 12
		$|B|=3^6$
	$A\cap B$: set of strings starting with 0 and ending with 12
		$|A\cap B|=3^5$
	By the **inclusion-exclusion principle**, $|A\cup B|=|A|+|B|-|A\cap B|=3^7+3^6-3^5$