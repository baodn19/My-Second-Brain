---
created: March 26th 2026
categories:
  - "[[Concepts]]"
modified: March 26th 2026, 1:37:47 pm
tags:
  - data-structure
---
- *Definition:* sorted [[binary tree]], with the key of each internal node being greater than all the keys in the respective node's left subtree and less than the ones in its right subtree.
- *Characteristic:*
	- [[in-order traversal]] always yields the keys in sorted (ascending) order
- *Deletion:* 
	- *2 children:* replace it with either its **in-order predecessor** (the maximum value in the left subtree) or its **in-order successor** (the minimum value in the right subtree).
- *Worst case search time:*
	- *[[perfect BST]]:* $O(\log n)$
	- Non-perfect BST: $O(n)$
- *Type:*
	- *Full:* a node either has none or 2 children
	- *Complete:* each level is filled with nodes strictly left-to-right