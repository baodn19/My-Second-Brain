---
created: 2026-02-15
categories:
  - "[[Class Lectures]]"
modified: February 15th 2026, 4:49:01 pm
class:
  - "[[COP4530]]"
tags:
  - computing-theory
  - data-structure
---
## Section 1
1. section1-1.cpp
2. Below is the hierarchical inheritance structure:
- Level 0 (base class): `Person` includes the basic information that everyone has. All the other classes are derived from this class.
- Level 1:  `Student` and `Faculty` inherit from `Person` and are separated by learners and teachers.
- Level 2:
	- `UndergraduateStudent` and `GraduateStudent` are children of `Student` class. They are different in degree level.
	- `Professor` and `Instructor` inherit from `Faculty` which are distinguished by roles.
3. Member variables for each class
- **Person**
    - `string name`
    - `int age`
    - `string gender`
- **Student** (Inherits from Person)
    - `string major`
    - `string id`
    - `float gpa`
- **Faculty** (Inherits from Person)
    - `string department`
    - `float salary`
- **UndergraduateStudent** (Inherits from Student)
    - `string yearLevel` 
- **GraduateStudent** (Inherits from Student)
    - `string thesisTitle`
- **Professor** (Inherits from Faculty)
    - `string research`
    - `bool tenured`        
- **Instructor** (Inherits from Faculty)
    - `int courseLoad`
## Section 2
4. 
```
Read it. 
Ship it. 
Buy it. 
Read it. 
Box it. 
Read it.
```
- *Explanation:*
	- Initializing:
		- `mid` points to a `State` object
		- `md` points to a `Maryland` object
		- `obj` points to a `Place` object
		- `usa` points to a `Region` object
	- Execution:
		- `md->printMe()`: calls `Maryland::printMe`. **Output: "Read it."**
		- `mid->printMe()`: calls `State::printMe`. **Output: "Ship it."**
		- `(dynamic_cast<Place*>(obj))->printMe()`: `obj` is pointing to a `Place` object; casts `Object*` to `Place*`; calls `Place::printMe`. **Output: "Buy it."**
		- `obj = md`:  `obj` points to a `Maryland` object
		- `(dynamic_cast<Maryland*>(obj))->printMe()`: `obj` is pointing to a `Maryland` object; downcasts `Object*` to `Maryland*`; calls `Maryland::printMe`. **Output: "Read it."**
		- `obj = usa`: `obj` points to a `Region` object
		- `(dynamic_cast<Place*>(obj))->printMe()`: `obj` is pointing to a `Region` object (which inherits `Place`); calls `Region::printMe`. **Output: "Box it."**
		- `usa = md`: `usa` points to a `Maryland` object
		- `(dynamic_cast<Place*>(usa))->printMe()`: `usa` is a `Place` object and is pointing to a `Place` object; casts `Object*` to `Place*`; calls `Maryland::printMe`. **Output: "Read it."**
## Section 3 
5.  section3-5.cpp
## Section 4
6. section4-6.cpp