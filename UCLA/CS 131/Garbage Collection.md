---
id: "Garbage Collection"
aliases:
  - "Approaches to Garbage Collection"
tags:
  - "CS131"
---

- When a value or an object on the heap is no longer referenced, the program
  (eventually) detects that and frees the memory at runtime
- Advantages:
  - No memory leaks
  - No dangling pointers
  - No double-free bugs (freeing after it's already been deleted)
  - No manual memory management
- However, reasoning about garbage collection is tricky, since it is
  non-deterministic

## Approaches to Garbage Collection

- Only free an object's memory when that object has no more references to it,
  e.g. when the object goes out of scope

## Mark and Sweep

- In the "marking" phase, the garbage collector identifies all objects that are
  still referred to (read: in-use)
  - The object is either:
    - A root object (somewhere on the stack)
    - Reachable from a root object via pointers/references
- In the "sweeping" phase, the garbage collector scans the entire heap, and
  frees all blocks that are not in-use
- Benefits:
  - Simple
  - No trouble with cyclic references (when two objects refer to one another)
- Drawbacks:
  - Program must be paused during garbage collection (bad for real-time
    programs)
  - Dealing with large amounts of data can lead to thrashing
  - Causes memory fragmentation
  - Unpredictable

## Mark and Compact

- Instead of "sweeping" the unused memory, we "compact" it by moving all valid
  chunks of memory to a contiguous block, and freeing everything else
- Benefits:
  - Deals with fragmentation a lot better
- Drawbacks:
  - Is more complex/slower

## Unpredictability

- Garbage collection is non-deterministic because it relies on _memory pressure_
  (when the program requires memory)
- We can't predict when (or even _if_) the garbage collector will run
  - We can't _really_ rely on destructors

## Reference Counting

- Each object has a hidden counter that tracks how many references there are to
  it
- References only change when:
  - A variable is assigned to
  - When an object goes out of scope
- Benefits:
  - Simple
  - Usually real-time (since reclamation is _usually_ instant)
  - More efficient utilization of memory since unused objects are freed
    immediately
- Drawbacks:
  - Cyclic references cannot be handled by reference counting, since the counter
    will never reach 0
  - A "cascade" can happen if one object has references to many other objects,
    freezing the computer
    - Some languages amortize deletion over time, but this is non-deterministic
  - Updating counts must be thread-safe
  - Updating on every operation could be expensive
