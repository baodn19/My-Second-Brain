---
categories:
  - "[[Concepts]]"
created: March 14th 2026
modified: March 14th 2026, 10:43:38 pm
tags:
  - computing-theory
---
- *Definition:* schedule coroutines to run ASAP and simultaneously
	- If one task is waiting for something, another task can start
- `... = asyncio.create_task(<corountine object>)`: create a task for each coroutine object
- `... = await asyncio.gather(<corountine object1>, ...)`: create a task for multiple objects and execute them
	- Return a **list**
	- Bad for error handling, doesn't cancel when one coroutine fails
- *Task Group:* has error handling, cancel if one coroutine fails
	- Execute all the tasks added to the group
``` python
async with asyncio.TaskGroup() as tg:
	... = tg.create_task(<corountine object>)
	...
```
