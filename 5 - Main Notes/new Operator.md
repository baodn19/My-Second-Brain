---
categories:
  - "[[Code Syntax]]"
created: January 26th 2026
modified: January 26th 2026, 2:56:51 pm
tags:
  - computing-theory
  - operator
---
## Overview
- Allocates memory from the free store 
- Returns a [[Pointers]] to the allocated object
- Memory is allocated from the [[free store]] 
- It exists even after leaving the statement 
- It will remain until [[delete Operator]] is called

## Syntax
- `Type* p = new Type;` : p stores the address; `*p` refers to the actual object
- *Initializing members:* `p-><member> = <value>;`