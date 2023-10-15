---
id: "Multi-Cycle Design"
aliases: []
tags:
  - "CSM151B"
---

- By breaking down each instruction into multiple stages (each taking one clock
  cycle), we can elide certain cycles from shorter instructions
  - For example, `add` doesn't require memory access, and could be done in 3
    cycles while `load` would take the "full" 4
  - We can greatly improve clock speed, but now each instruction will take
    multiple clock cycles to execute
- However, this is very complicated and adds a lot of complexity
  - Intermediate states must be stored in register
