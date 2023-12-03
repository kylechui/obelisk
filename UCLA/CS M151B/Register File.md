---
id: Register File
aliases: []
tags:
  - CSM151B
---


- Basically just an array of registers
- Can be indexed into, e.g. $x_i$ is the $i$th register
  - Since there are 32 registers in [[RISC-V]], we need 5 bits to indicate which
    register we want to select
- It is connected to the datapath, and automatically destructures each
  instruction to get register indices
  - Sometimes this computation is unnecessary, but it reduces latency because it
    is done in parallel

