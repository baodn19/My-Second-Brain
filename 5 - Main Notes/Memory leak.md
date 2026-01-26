---
categories:
  - "[[Concepts]]"
created: January 26th 2026
modified: January 26th 2026, 3:05:14 pm
tags:
  - computing-theory
---
- *Occurs when:*
	- Memory is dynamically allocated using [[new Operator]] 
	- The [[Pointers]] to that memory is lost without calling delete 
	- The memory becomes inaccessible but still occupied
- *Consequence:*
	- The original object still exists in memory 
	- No pointer refers to it anymore 
	- It cannot be deleted
- *How it happens:*
Before reassignment: p ───>Passenger Object A
After reassignment: p ───> Passenger Object B
	Passenger Object A is unreachable (leak)