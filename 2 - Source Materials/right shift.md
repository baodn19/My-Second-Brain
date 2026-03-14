---
categories:
  - "[[Concepts]]"
created: March 14th 2026
modified: March 14th 2026, 12:27:31 am
tags:
  - computer-architecture
---
- *Definition:* shift byte a over b bits to the right
- *Annotation:* a >> b
	- *Application:* a is divided by $2^b$ (Faster than division operations as they are [[CPU]] instructions)
- *Example:*
	- $10_{10}$ = $00001010_{2}$
	- $00001010_{2}$ >> 1 = $00000101_{2}$ = $5_{10}$
	- $10_{10}$ >> 1 = $5_{10}$ 