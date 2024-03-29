---
id: "Datapath"
aliases: []
tags:
  - "CSM151B"
---

- In general, all possible signals are generated in parallel, since it is better
  to perform unnecessary work in exchange for lower latency
- A signal `PCSrc` is created depending on whether the instruction is a `jump`
  instruction or not, and is used to multiplex whether we use:
  - The current program counter and hard-code the sum `PC + 4` (branchless case)
  - The output of the [[Arithmetic Logic Unit|ALU]] as the next instruction
- The [[Arithmetic Logic Unit|ALU]] takes in its inputs, and using instruction
  information from the [[Controller|controller]], computes the result
- Our immediates from the instruction need to be processed by an immediate
  generator, which sign-extends them to 32 bits
  - The generator uses bits 5 and 6 from the instruction as input for a 3:1
    multiplexer which selects which immediate to use
- A signal `ALUSrc` is created depending on whether the input is a register or
  immediate-type instruction, and that is used to multiplex the input of the
  [[Arithmetic Logic Unit|ALU]]
