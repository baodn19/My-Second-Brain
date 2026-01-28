---
created: January 28th 2026
categories:
  - "[[Code Syntax]]"
modified: January 28th 2026, 12:10:15 pm
tags:
  - computing-theory
  - cpp
---
## Overview
- *Improvement over [[array]]:*

| Feature          | Array | Vector         |
| ---------------- | ----- | -------------- |
| Size             | Fixed | Dynamic        |
| Bounds checking  | No    | Yes ([[at()]]) |
| Can grow/ shrink | No    | Yes            |
| STL support      | No    | Yes            |

## Syntax
- *Initialize:* `vector vector_name;`
```cpp
vector<int> v = {1, 2, 3, 4};
vector v(5); // size 5, default values 0 
vector v(5, 10); // size 5, all values 10
```
- *Add element:* [[push_back()]]
```cpp
v.push_back(10); 
v.push_back(20);
```