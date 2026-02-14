---
created: 2026-02-02
categories:
  - "[[Class Lectures]]"
modified: February 4th 2026, 9:43:49 am
class:
  - "[[COP4530]]"
tags:
  - computing-theory
---
## Section 1
1. The `main()` marks the start of the C++ program. The function is called when the program is executed.  `main()` returns an integer to the [[operating system]] to indicate the program's [[exit status]]. 
2. `int`: store integers ($int \in \mathbb{Z}$)
	`double`: store double-precision floating-point number
	`char`: store a single ASCII character
	`bool`: store truth values (TRUE/ FALSE)
3. section1-3.cpp
4. *Situations `double` is preferred:* scientific calculations or financial applications to avoid rounding errors 

| Difference | float                                | double                               |
| ---------- | ------------------------------------ | ------------------------------------ |
| Type       | single-precision floating-point type | double-precision floating-point type |
| Size       | 4 bytes                              | 8 bytes                              |
| Precision  | ~7 decimal digits                    | ~15 decimal digits                   |
## Section 2
5. section2-5.cpp
6. *Difference:* `while` loop checks condition before executing the body, and `do-while` loop executes the body once before evaluating the condition
``` cpp
x = 0;

// while loop: never run => x = 0
while (x > 0) { x--; } 

// do-while loop: runs once => x = -1
do { x--; } while (x > 0);
```
7. section2-7.cpp
8. section2-8.cpp
## Section 3
9. 
``` cpp
// Declaration
double calculateArea(double length, double width);

// Definition
double calculateArea(double length, double width) {
    return length * width; // Area
}
```
10.  Function overloading in C++ allows many functions with the same name to have different parameters
``` cpp
int subtract(int a, int b) { return a - b; }
double subtract(double a, double b) { return a - b; }
```
11. *Difference:* Pass-by-value copies the variables inside the function and make changes that don't affect the original variables. Pass-by-reference passes the address of the original variable which can be affected by changes in the function.
- *Preference for pass-by-reference:* need to modify original variable or passing large objects
12. Default arguments are arguments with provided value in function declaration that can be used if the caller leaves out the corresponding argument.
``` cpp
int add(int x, int y = 10) { return x + y; } 

cout << add(9) << endl;
```
13. section3-13.cpp
## Section 4
 14. section4-14.cpp
 15. Encapsulation is organizing data and methods into a unit (a class). In C++ implementation, `private` hide internal data members and `public` share functions to interface with the data.
 16. Access specifiers:
- `public`: members can be accessed outside of class
- `private`: members can only be accessed within the class and declared friend classes
- `protected`:  members can only be accessed within the class and by derived classes, and isn't accessible from outside
 17. Inheritance let a derived class acquire properties and behaviors from a base class
 ``` cpp
 class Rectangle {
 private:
    double length;
    double width;

 public:
    // Set length and width
    void setValues(double l, double w) {
        length = l;
        width = w;
    }

    // Calculate area and perimeter
    double getArea() {
        return length * width;
    }

    double getPerimeter() {
        return 2 * (length + width);
    }
};

// Square inherits from Rectangle
class Square : public Rectangle {
public:
    void setSide(double s) {
        setValues(s, s); // Reuses Rectangle's method
    }
};
 ```
## Section 5
18. section5-18.cpp
19. A memory leak happens when dynamically allocated memory (using `new`) is not properly deallocated (using `delete`), leading to memory spaces that can't be accessed
- *Prevention:*
	- Always pair every `new` with `delete`
	- Use smart pointer `std::unique_ptr` or `std::shared_ptr` which automatically manage memory.
20. section5-20.cpp. `&` gets the address of a variable, and `*` gets the value stored at the pointer's address
## Section 6
21. section6-21.cpp. Exception handling deals with runtime errors without crashing
22. section6-22.cpp. `const` keyword specifies that a variable cannot be modified