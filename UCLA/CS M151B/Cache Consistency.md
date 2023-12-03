---
id: Cache Consistency
aliases: []
tags:
  - CSM151B
---

- Ordering parallel accesses between different addresses
  - Problem: Multiple cores reading/writing from/to memory can lead to incorrect
    ordering of memory operations and incorrectness
- Timing between two cores is the programmer's job to fix using synchronization
  techniques
- Sequential consistency (SC): What programmers expect
  - Processors see their own loads/stores in program order
  - Processors see others' loads/stores in program order
  - All processors see the same global load/store ordering
  - Too slow; can we reorder some operations?
- Total Store Order (TSO) Model
  - Each processor can move its own reads in front of its own writes (different
    addresses!)
    - Use a [[Load-Store Queue|LSQ]]
- There are other "weaker" consistency models that allow for more
  parallelism/re-ordering, but are more complex
- Solution: Use synchronization!
  - Programmer and/or hardware uses some primitives (e.g. locks) to solve
    timing/ordering problems
  - Producer-consumer model
    - Fences enforce that all instructions before it complete before the fence
      is executed (hardware)
    - Semaphore: Some barrier that synchronizes multiple cores (software)
  - Mutual exclusivity: Only one process has access to a shared region at a time
    - Mutex/lock: Acquire/release locks, guarantee that after a lock is released
      that all operations are done and changes are visible to all cores
    - Atomic instruction: Hardware primitive that guarantees that instructions
      are executed in-order and without interruption
