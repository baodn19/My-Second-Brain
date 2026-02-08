---
created: February 8th 2026
categories:
  - "[[Concepts]]"
modified: February 8th 2026, 10:39:25 am
tags:
  - deep-learning
  - machine-learning
  - computer-vision
---
- [[epoch]]
- [[batch]]
- *imgsz:* crop images to a square
	- *Effect:* increase can help detect small objects, small size might make image blurry
	- 32 must be a [[divisor]] of the size because the image gets [[downsample]] 5 times ($2^5=32$)