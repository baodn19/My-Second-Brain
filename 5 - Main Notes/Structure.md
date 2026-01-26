---
created: January 26th 2026
categories:
  - "[[Concepts]]"
  - "[[Code Syntax]]"
tags:
  - "#computing-theory"
  - "#data-structure"
modified: January 26th 2026, 2:54:35 pm
---
## Overview
- *Definition:* user-defined type
	- Groups related data w/ different types
	- Element: member/ field
- *Use case:* represents a **real-world entity**
- Structure vs [[Array]]:

| Feature       | Structure            | Array             |
| ------------- | -------------------- | ----------------- |
| Data types    | Different            | Same              |
| Member access | Name fields          | Index-based       |
| Meaning       | Represents an entity | Represents a list |
| Flexibility   | High                 | Low               |

## Syntax
- *Code define:*
```cpp
struct <struct_name> {
	<type1> <member1>
	...
}
```
- *Initializing:*
```cpp
<struct_name>.<member> = <value>
```
