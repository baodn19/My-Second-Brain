---
created: March 26th 2026
categories:
  - "[[Concepts]]"
modified: March 26th 2026, 12:20:47 pm
tags:
  - algorithm
---
- *Definition:* visiting every node in a [[binary tree]] level by level, starting from the root and moving from left to right. It is a specific application of **[[Breadth-First Search (BFS)]]**.
- *Algorithm:* utilizes a **[[Queue]]**
	1. **Initialize**: Create an empty queue and enqueue the root node.
	2. **Iterate**: While the queue is not empty:
	    - Dequeue the front node.
	    - Visit (process) the dequeued node.
	    - Enqueue the node's **left child** (if it exists).
        - Enqueue the node's **right child** (if it exists).