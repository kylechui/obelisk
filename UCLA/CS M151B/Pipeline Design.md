---
id: "Pipeline Design"
aliases: []
tags:
  - "CSM151B"
---

- Looking at the
  [[Performance and Pipelining|Iron Law of Processor Performance]], we see that
  we can try to decrease the following:
  - Number of instructions: Not very practical, as it's mostly a result of
    algorithms and compiler optimizations
  - Cycle time: Not very practical, as it's mostly a result of newer
    technologies/hardware
  - Cycles per Instruction: We will focus on this
- One approach is the [[Multi-Cycle Design]]
- An improvement is to use pipelining
  - Overlap instructions to decrease the "effective" cycles per instruction back
    down to 1
  - We can split our instructions into around 5 "steps", with registers in
    between steps to hold intermediate states
    - E.g. Instruction Memory, [[Register File]], [[Arithmetic Logic Unit|ALU]]
    - Fetch, Decode, Execute, Memory, Writeback
- An additional optimization we can perform is to use "half-cycle" operations,
  where we write a signal on the positive edge of the clock, and read on the
  negative edge
  - This opens us up to many potential [[Hazards]]
