---
created: March 14th 2026
categories:
  - "[[Concepts]]"
modified: March 14th 2026, 12:26:29 am
tags:
  - computing-theory
---
- *Why:*
	1. Memory management: 
	- Manage memory and lifetime of objects safely
	- In [[ROS2]], nodes and other ROS objects must be **shared resources**. The `std::sharded_ptr<rclcpp::Node>` ensures only one instance exists and is deallocated when done, avoiding memory leaks or premature destruction.
	2. Consistency with ROS2 API: most factory and API (like `create_client`) request or return `std::shared_ptr`
	3. Prevent dangling pointers or double frees
- *Smart Pointer:* `std::shared_ptr` 
	- *Definition:* a smart pointer that provides shared ownership of a dynamically allocated object through reference counting
	- *Mechanism:*
		- Reference counting:
			- A new `shared_ptr`: counter = 1
			- `shared_ptr` copied: counter++
			- `shared_ptr` destroyed: counter--
		- Auto deallocation: if counter == 0, the object is deleted and free memory
	- *Properties:* 
		- Copies **share** ownership (unlike `unique_ptr`)
		- See counter: use `<pointer>.use_count()` 