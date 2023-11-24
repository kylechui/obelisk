---
id: Memory
aliases: []
tags:
  - CSM151B
---

- Memory is organized as an array of registers
  - Since we wish for it to be byte-addressable, we might choose the width to be
    8 bits
  - The length then depends on the total size of memory
  - We use a multiplexer to read specific lines from memory
- There are a few different types of memory; the key thing is to remember size
  and speed are inversely correlated:
  - Registers (Latches/Flip-flops):
    - Very fast (parallel access)
    - Very expensive (10s of transistors/bit)
  - Static RAM (SRAM):
    - Relatively fast (but one data word at a time)
    - Expensive (6+ transistors/bit)
  - Dynamic RAM (DRAM):
    - Slower, one word at a time, reading destroys content, needs special
      process to manufacture
    - Cheap (1 transistor + 1 capacitor/bit)
  - Disk (SSD, HDD):
    - Much slower, non-volatile
    - Very cheap
- The memory is organized in a [[Memory Hierarchy|memory hierarchy]]
