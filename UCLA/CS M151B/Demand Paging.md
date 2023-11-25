---
id: Demand Paging
aliases: []
tags:
  - CSM151B
---

- We treat DRAM as a cache our disk, and "swap" pages between the two
  - We want to keep the most frequently used bytes in DRAM
    - If the page we want is not in DRAM, then we experience a "page fault", and
      pay a severe penalty
    - We can use a "valid" bit to indicate whether or not a page exists in DRAM
      or not
- Same basic issues as caches:
  - What pages should we swap from DRAM to disk when we experience a page fault?
- OS handles everything, since it is much easier (and is fast enough)
  - Pseudo-LRU replacement policy
