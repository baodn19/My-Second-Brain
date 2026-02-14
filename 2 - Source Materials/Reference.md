---
categories:
  - "[[Code Syntax]]"
created: January 26th 2026
modified: January 26th 2026, 3:10:12 pm
tags:
  - computing-theory
---
## Overview
- A reference is an alternative name (alias) for an existing variable
- *Property*: must refer to an object; must be initialized; act as original variable
- *Why:*
	- Function arguments 
	- Returning values from functions 
	- Avoiding unnecessary copying 
	- Writing cleaner, safer code
- *Memory Safety:*
	- [[null pointer]] → powerful, flexible, risky; use only when necessary 
	- References → safer, simpler, limited; use when possible
## Syntax
- `T& <refName> = <variable>`