---
categories:
  - "[[Concepts]]"
created: March 14th 2026
modified: March 14th 2026, 10:43:19 pm
tags:
  - computing-theory
---
- *Types:* 
	- *Coroutine function:* `main()`
	- *Coroutine object:* returned by the function above. Needs to be **awaited** to execute
- `asyncio.run(<corountine object>)`: start **event loop** by running **coroutine object**. The code handle the awaiting to let the object execute.
- `... = await <corountine object>`: step necessary for the **coroutine object** to execute
	- All the following `await` has to wait for the current `await` to finish running
	- `await asyncio.sleep(<seconds>)`: delay the program 
- *Define coroutine function:*
``` python
async def main():
	print("...")
```
