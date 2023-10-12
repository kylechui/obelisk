---
id: "Controller"
aliases: []
tags:
  - "CSM151B"
---

- Based on the `opcode`, `funct7`, and `funct3` regions of the instruction, the
  controller can disambiguate which instruction it's looking at
  - Under certain circumstances, we can even avoid checking `funct3` and
    `funct7` because the `opcode` is already unique enough
  - With this information, we know if we are supposed to load
    [[Register File|from registers]], [[Loading Data From Memory|from memory]],
    or an [[Loading Immediates|immediate]]
  - It essentially takes the 32-bit instruction as input, and outputs a bunch of
    control signals (e.g. register indices, read/write signals, etc.)
