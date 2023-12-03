---
id: Multicore
aliases: []
tags:
  - CSM151B
---

- After hitting the [[Power Wall|power wall]], we kept speeding up computing by
  using [[Thread-level Parallelism|thread-level]], task-level, and program-level
  parallelism
- However, we are still bottlenecked by the parts of the program that we can't
  parallelize
  - This is also referred to as _[[Amdahl's Law|Amdahl's Law]]_
  - [[Superscalar]] pipelines are typically _underutilized_
    - [[Simultaneous Multi-Threading|Simultaneous Multi-threading (SMT)]]
    - Another approach is to [[Multi-tasking|multi-task]]
- We are currently in the end of the multicore era, due to "dark silicon"
  - We can't enable all parts of a chip at the same time due to thermal
    limitations
  - It's over for [[Moore's Law]]
- Cores communicate via memory, but how can we share memory in a
  [[Cache Coherency|coherent]] and [[Cache Consistency|consistent]] fashion?
  - Cache can be shared between cores, or private to each core (or hybrid!)
