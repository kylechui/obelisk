---
id: "Concurrency"
aliases:
  - "Models for Concurrency"
tags:
  - "CS131"
---

- Concurrency is a paradigm where a program is decomposed into simultaneously
  executing tasks
  - Operations on shared mutable state is dangerous!
  - Our goal is to improve the performance, while keeping the code _deterministic_
- Multiplexing on a single core can still boost performance because a lot of
  tasks require waiting (e.g. IO)

## Models for Concurrency

- Multi-threading: Program creates multiple threads, which run concurrently
  (potentially in parallel)
  - The programmer "launches" one or more functions in their own threads, and
    the OS schedules the execution across available CPU cores
- Event Driven: A program has a queue of functions to run, and an infinite loop
  that dequeues/runs the functions
  - When an event occurs, a new function is added to the queue that handles the
    event

## The Fork-Join Pattern

- A concurrent version of divide-and-conquer, often used recursively
- We "fork" one or more tasks to execute concurrently
- Then, after they complete we "join" their results and proceed
- Note: Python's implementation of concurrency is pretty bad because of _Global
  Interpreter Lock_

## hi

- A _callback function_ is a function that is called when a certain event
  occurs, e.g. timer expiration or button press
- Programs with UIs don't necessarily run top-to-bottom because users can
  interact with the program at any location in any order
  - They use an _event loop_
