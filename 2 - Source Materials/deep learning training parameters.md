---
created: February 8th 2026
categories:
  - "[[Concepts]]"
modified: February 12th 2026, 5:15:57 pm
tags:
  - deep-learning
  - machine-learning
  - computer-vision
  - umich
---
- *Definition:* hierarchical [[learning]] algorithms with many "layers", loosely inspired by the brain
- [[epoch]]
- [[batch]]
- *imgsz:* crop images to a square
	- *Effect:* increase can help detect small objects, small size might make image blurry
	- 32 must be a [[divisor]] of the size because the image gets [[downsample]] 5 times ($2^5=32$)