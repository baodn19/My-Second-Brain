---
created: March 11th 2026
categories:
  - "[[Concepts]]"
modified: March 11th 2026, 11:21:13 pm
tags:
  - logic-gate
---
- [[NAND]] implementation (active-low):

| $\bar{S}$ | $\bar{R}$ | $Q^+$      |
| --------- | --------- | ---------- |
| 0         | 0         | $Q_{prev}$ |
| 0         | 1         | 1          |
| 1         | 0         | 0          |
| 1         | 1         | Q          |
