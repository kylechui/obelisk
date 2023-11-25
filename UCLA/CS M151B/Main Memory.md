---
id: Main Memory
aliases: []
tags:
  - CSM151B
---

- We usually call the combination of the DRAM and disk as "main memory"
  - DRAM is volatile, slow, large
  - Disk is non-volatile, very slow, very large
- Access to the main memory is _always_ a hit
  - Although there is a huge latency difference between DRAM and disk
  - We use [[Demand Paging|demand paging]] to maintain the differences between
    the two
- To run different programs in a computer, we must have
  [[Memory Management|memory management]]
