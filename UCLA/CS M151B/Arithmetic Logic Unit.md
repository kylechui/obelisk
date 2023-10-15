---
id: "Arithmetic Logic Unit"
aliases: []
tags:
  - "CSM151B"
---

- The ALU uses a `ALUOp` signal (4 bits) to determine which operation to do on
  the two input values
  - For our implementation, we only really need two bits to disambiguate between
    `add`, `subtract`, `and`, `or`, etc.
    - `00`: `add`
    - `01`: `subtract`
    - `10`: Check `funct3` and `funct7`
  - The `ALUOp` then outputs a 4 bit signal to the actual arithmetic logic unit
