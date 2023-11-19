---
id: Reducing Miss Penalty
aliases: []
tags:
  - CSM151B
---

- Use a load-store queue: Delay writes to memory by first writing to a write
  buffer and then moving onto the next instruction
  - No wait for stores needed
  - Lower miss penalty for loads
  - More overhead
  - For stores, if the data already exists in the cache:
    - Write through: Update memory and cache on every write
    - Write back: Update the memory only when the line is evicted
  - If the data does not exist:
    - Write allocate: Bring it to the cache
    - Write no allocate: Don't bring it to the cache
  - Oftentimes we pair write back with write allocate, and write through with
    write no allocate
- Early restart: Instead of waiting for all bytes in a block to arrive, forward
  data to the CPU as it comes in
  - Critical word first: Optimization where the requested byte is read first
- If we have multiple cache layers, then our miss penalty gets scaled by the
  miss rate
- Sub-blocking: Keep larger block sizes, but divide it into smaller sub-blocks;
  bring a subset of them on a miss
  - Increasing block size directly increases miss penalty!
  - Lower miss rate/penalty, but more complex
