---
id: "Instruction Set Architecture"
aliases:
  - "ISA"
tags:
  - "CSM151B"
---

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
