---
id: "Instruction Lifecycle"
aliases: []
tags:
  - "CSM151B"
---

- Each instruction can be thought of as a transition function between states in
  a [[Finite State Machine|finite state machine]]
- The steps in the lifecycle:
  - The instruction is fetched from instruction memory
  - Operands are loaded
    - From [[Register File|register file]],
      [[Loading Data From Memory|from memory]], and by
      [[Loading Immediates|loading immediates]]
  - The [[Controller|controller]] discerns which instruction is performed, and
    executes it
  - Results are stored (in memory or in the [[Register File|register file]])
  - Program counter should be updated
    - Sequentially, via a jump, or via a branch?
