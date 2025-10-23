# Learning Resources
- https://www.youtube.com/watch?v=Qb9s3UiMSTA&t

# Overview
- *Definition*: Handling multiple tasks at once (especially those with **big waiting time**)
- *When to use Asyncio, threads, or processes:*
	- Asyncio: Tasks that wait a lot (network requests, reading files); do many concurrent tasks with low CPU usage
	- Threads: tasks that wait and share data; useful for IO bound and less CPU intensive task
	- Process: CPU heavy task in parallel

# Key Concepts
## Event loop: Core that manage and distribute tasks. Each task goes in to run. If they need to wait for data, another task runs.
## Coroutines:
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

## Tasks:
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

## Synchronization:
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

## Futures:
- *Usage:* not something to write on your own, used for low-level programming

# Usage:
- *Requirement:* Python >=3.11
- `import asyncio`: import

