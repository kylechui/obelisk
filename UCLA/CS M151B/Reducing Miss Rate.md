---
id: Reducing Miss Rate
aliases: []
tags:
  - CSM151B
---

- Increase block size to exploit more spatial locality
- Increase associativity
- [[Prefetching|Prefetch instructions]], e.g. if we can guess the access pattern
  then we can fetch data before it's needed
- Victim cache: Have a few extra temporary bits of memory to store heavily
  conflicting addresses (basically just extending the cache size)
  - Can store the most recently used 10-12 addresses
  - Reduces conflict misses, but adds overhead and makes the design more
    complicated
- Compiler/software
  - Re-order instructions to increase locality (row-major vs. column-major
    access)
  - Combine loops with similar behavior
  - Use tiling
  - Utilize generated code to improve [[Prefetching|prefetching]]
- Replacement policy: Choose which elements to evict
  - There's a storage vs. accuracy tradeoff
