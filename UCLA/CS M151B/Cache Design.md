---
id: Cache Design
aliases: []
tags:
  - CSM151B
---

- When flushing old instructions, we have multiple designs:
  - Log-based: Store "old" destination register and restore RAT one instruction
    at a time
  - Checkpoint-based: Have two versions of each table for "messy" and
    "architectural"; use "messy" values for the reservation station and when
    it's safe to do so copy to the "architectural" table
    - If we need to revert stuff, just copy from "architectural" back to "messy"
- How do we deal with memory [[Hazards|hazards]]?
  - Renaming registers doesn't solve this, because we are dealing with memory
    address collisions, not register collisions
  - RAW: Reading before writing is finished
  - WAW: Double writing to an address
  - WAR: Loading before storing
- We add a [[Load-Store Queue|load-store queue]]
- Cache hit: Requested data exists inside cache
- Cache miss: Requested data does not exist inside cache
- Average Access Time (AAT): HitTime + MissRate \* MissPenalty
- Two main kinds of cache:
  - Direct-mapped: Map `n` to `n mod 2^k`
    - Susceptible to alternating access pattern
    - Better hit time, but worse miss rate
  - Fully associative: Map `n` to the first open region of the cache
    - Better miss rate, but worse hit time
- We can combine the properties of both into a set-associative cache
  - We have a mapping from index to a few columns of space, instead of just one
- When evicting items from the cache, we don't have a choice for directly mapped
  caches but we do for fully-associative and set-associative
  - When we have a choice, we can use LRU
- Compulsory miss: The miss associated with the initial fetch of some data
- Capacity miss: The miss associated with limited capacity in a
  fully-associative cache
- Conflict miss: The miss associated with index bit matching in a set
  associative or directly-mapped cache
- We want to [[Reducing Miss Rate|reduce miss rate]],
  [[Reducing Hit Time|reduce hit time]], and
  [[Reducing Miss Penalty|reduce miss penalty]]
- Inclusive cache: Faster layers are a subset of slower layers
  - Easier to find data, but inefficient space usage
- Exclusive cache: Data exists in exactly one layer
  - Harder to find data, but efficient space usage
- Princeton (more common): Unified instruction and data memory
- Harvard: Separate instruction and data memory
