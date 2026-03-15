---
created: March 14th 2026
categories:
  - "[[Concepts]]"
modified: March 14th 2026, 10:44:19 pm
tags:
  - computing-theory
---
# Overview
- *Definition*: Handling multiple tasks at once (especially those with **big waiting time**)
- *When to use Asyncio, threads, or processes:*
	- [[Asyncio]]: Tasks that wait a lot (network requests, reading files); do many concurrent tasks with low [[CPU]] usage
	- Threads: tasks that wait and share data; useful for IO bound and less CPU intensive task
	- Process: CPU heavy task in parallel

# Key Concepts
- *Event loop:* Core that manage and distribute tasks. Each task goes in to run. If they need to wait for data, another task runs.
- *[[coroutines]]*
- *[[asynchronous tasks]]*
- *[[asynchronous tasks synchronization]]*
