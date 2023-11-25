---
id: Translation Lookaside Buffer
aliases: []
tags:
  - CSM151B
---

- A local cache that stores some mappings from virtual page addresses to
  physical page addresses, to avoid multiple dereferences when walking the
  [[Page Table|page table]]
- If the address is found in the TLB, then we have a "TLB hit", and the request
  can be fulfilled in a single cycle
- If not, then we have a "TLB miss", and we need to walk the
  [[Page Table|page table]] to refill the TLB with the new address
- The "TLB Reach" is the size of the largest virtual address space that can be
  mapped to by the TLB
  - For example, if we have 4KB pages and 64 entries, then the TLB reach is 256
    KB
- Usually 32--128 entries, fully associative
