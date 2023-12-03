---
id: Cache Coherency
aliases: []
tags:
  - CSM151B
---

- Ordering of parallel accesses to the same address
  - Problem: We may end up with incorrect copies in each private cache
    - This can't be solved via software, since software isn't aware of the
      existence of caches
- A system is coherent if:
  - Reads return what data is written
  - Reads of writes from other processors work fine
  - Successive writes are order-invariant
- We use a coherency protocol
  - "Snoop" the caches for each read/write, and invalidate the cache if a new
    write comes along
    - Not very scalable
  - Write miss: Address is invalidated in all other caches before write is
    performed
  - Read miss: If a dirty copy is found in another cache, perform a write-back
    to memory before reading; otherwise just read from memory
  - Only one core can be in the `M`(odified) state at any given time, all the
    other cores are in the `I`(nvalid) state
    - Write-back and update memory before leaving `M` state
    - Since we can have multiple readers, we add the `S`(hared) state
      - Since reading from memory is expensive, we can introduce another
        `F`(orwarder) state to directly share data between caches
    - We can also go to an `E`(xclusive) state, if we modify memory in one core
      but never update/read in others
      - This elides a broadcast, making it faster
    - Alternatively, we can go to an `O`(wner) state that can forward directly
      to other caches
    - Three possible paths:
      - I -> E -> F
      - I -> M -> O
      - I -> E -> M (silent)
  - Directory-based Coherence Protocol: Directory tracks copies of cached lines
    and their states, avoiding broadcasting
    - On a miss, find the directory and communicate with necessary nodes
- False sharing: We need blocks but coherence is done at the line-level
  - Coherence miss: Block is invalidated since the line got invalidated, but the
    data for that block hasn't changed
