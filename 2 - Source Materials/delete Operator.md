---
categories:
  - "[[Code Syntax]]"
created: January 26th 2026
modified: January 26th 2026, 2:59:31 pm
tags:
  - computing-theory
  - operator
---
## Overview
- Destroys the object and returns memory to the [[free store]]
- Only use delete on objects created with [[new Operator]]
- *Common errors:*

| Mistake               | Result               |
| --------------------- | -------------------- |
| Forgetting delete     | [[Memory leak]]      |
| Using delete on array | Undefined behavior   |
| Deleting twice        | Program crash        |
| Using after delete    | [[Dangling pointer]] |

## Syntax
`delete p;`