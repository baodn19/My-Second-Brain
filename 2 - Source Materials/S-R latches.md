---
created: March 11th 2026
categories:
  - "[[Concepts]]"
modified: March 12th 2026, 9:57:09 am
tags:
  - logic-gate
---
- *Definition:* a set-reset [[latch]] using 2 logic gates
- [[NAND]] implementation (active-low):

| $\bar{S}$ | $\bar{R}$ | $Q^+$      |
| --------- | --------- | ---------- |
| 0         | 0         | $Q_{prev}$ |
| 0         | 1         | 1          |
| 1         | 0         | 0          |
| 1         | 1         | Q          |
- [[NOR]] implementation (active-high):

| S   | R   | $Q^+$      |
| --- | --- | ---------- |
| 0   | 0   | $Q_{prev}$ |
| 0   | 1   | 0          |
| 1   | 0   | 1          |
| 1   | 1   | Q          |