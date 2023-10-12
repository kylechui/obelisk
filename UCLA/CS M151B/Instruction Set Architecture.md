---
id: "Instruction Set Architecture"
aliases: []
tags:
  - "CSM151B"
---

- An ISA is basically just an interface for what operations the
  [[Microarchitecture|hardware]] promises to implement
- The software will always provide some program that contains a list of known
  instructions, and the hardware only needs to promise to execute those
  instructions
  - This instruction set is called the instruction set architecture (ISA)
  - The ISA allows the hardware and software to evolve/change _independently_
- The software sees:
  - A functional description of the hardware:
    - Storage locations (e.g. memory)
    - Operations (e.g. add)
- The hardware sees:
  - A list of instructions and their order
- ISAs are typically designed with some microarchitectural style in mind, but
  can be implemented using any style
  - This class focuses on [[RISC-V]], which utilizes the hardwired, pipelined styles
