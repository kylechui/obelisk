---
id: "Multicore"
aliases: []
tags:
  - "CSM151B"
---

- After hitting the [[Power Wall|power wall]], we kept speeding up computing by
  using thread-level, task-level, and program-level parallelism
- However, we are still bottlenecked by the parts of the program that we can't
  parallelize
  - This is also referred to as _Amdahl's Law_
- We are currently in the end of the multicore era, due to "dark silicon"
  - We can't enable all parts of a chip at the same time due to thermal
    limitations
  - It's Joever for [[Moore's Law]]
