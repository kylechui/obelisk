---
id: "Control Flow"
aliases: []
tags:
  - "CSM151B"
---

- Normally, we are given a list of instructions and just execute them top to
  bottom
- To implement control flow, we have a program counter (PC register) that points
  to the address of the next instruction
  - This is how conditionals/loops/functions/etc. are implemented
  - Function returns are implemented using [[Linking|linking]]
- There are two main types of instructions for managing control flow in
  [[RISC-V]]:
  - Jump: Unconditional jump to some address
  - Branch: Jump to some address if a condition is satisfied
