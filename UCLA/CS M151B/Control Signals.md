---
id: "Control Signals"
aliases: []
tags:
  - "CSM151B"
---

- `RegWrite`: Are we writing to register file?
- `ALUSrc`: Are we using `rs2` or an immediate?
- `ALUOp`: Which ALU operation are we doing?
- `MemRead, MemWrite`: Are we performing a load/store?
- `MemtoReg`: Is the value that's going to be written to the register file
  coming from memory or the ALU?
- `PCSrc`: Did we branch?
