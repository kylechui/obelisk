---
id: Page Table
aliases: []
tags:
  - CSM151B
---

- Maps virtual page numbers to physical page numbers
  - We assume the page offset remains unchanged, which is why we don't need to
    map entire addresses
  - Each entry in the page table is called a page table entry (PTE)
    - We can also store some protections and flags in each PTE, e.g.
      write/read/execute, ownership
  - Use a base register to figure out which process is indexing into the page
    table
- We can compress these page tables by using a hierarchical page table
  - Idea: Store the page table as a page table, i.e. page tables that map to
    other page tables
  - This actually normally increases the amount of memory that we are using
    - Since we assume that virtual memory is quite _sparse_, we don't actually
      have that many intermediary page tables, allowing us to significantly cut
      on memory usage
  - This also increases the time for "walking" the page tables, since we must
    perform multiple dereferences
    - Solution: Cache most recent translations in the
      [[Translation Lookaside Buffer|Translation Lookaside Buffer (TLB)]]
    - We cannot access L1 before the TLB because L1 stores physical addresses,
      while TLB maps virtual addresses
      - We can't store virtual addresses in L1 because multiple programs could
        have the same virtual address (aliasing), causing conflicts and
        correctness issues
      - However, we can access them in parallel using a Virtually-indexed
        Physically-tagged Cache
        - Use the offset in the address to index into L1 cache and retrieve the
          line/tag that you want, to see if there is a hit
