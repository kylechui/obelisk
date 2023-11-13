---
id: "Register Renaming"
aliases: []
tags:
  - "CSM151B"
---

- We have a limited number of architectural registers (e.g. 32 in
  [[RISC-V|RISC-V]])
- We have much more physical registers
  - One architectural register can be assigned to multiple physical registers
- We implement this via Reigster Alias/Map Table (RAT)
  - One entry per architectural register
  - Each register stores the physical location of the most recent version of the
    logical register
  - For a destination logical register, we assign a new physical register from a
    pool of free registers
    - Don't put used registers back into the "free" pool until the instruction
      has been retired!
  - For each source logical register, we check the table
