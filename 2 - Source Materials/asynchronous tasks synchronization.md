---
categories:
  - "[[Concepts]]"
created: March 14th 2026
modified: March 14th 2026, 10:43:54 pm
tags:
  - computing-theory
---
- `<Lock> = asyncio.Lock()`: check if other coroutine is using the lock, if not: execute the `<code block>`. Others coroutine have to wait until the `<code block>` is finished
``` python
async with <Lock>:
	<code block>
```
- `<Semaphore> = asyncio.Semaphore(<# of coroutines>)`: allow `<# of coroutines>` to access one resource
``` python
async with <Semaphore>:
	<code block>
```
- `<Event> = asyncio.Event()`: similar to boolean flag
	- `<Event>.set()`: set to true
	- `await <Event>.wait()`: wait for the event to be set to true

