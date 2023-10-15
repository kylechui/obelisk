---
id: "Performance and Pipelining"
aliases: []
tags:
  - "CSM151B"
---

- The most important indicator of performance is the length of the critical path
  in the [[Datapath|datapath]]
  - The longest delay determines the clock period
  - This is the `load` instruction: Instruction memory ->
    [[Register File|register file]] -> [[Arithmetic Logic Unit|ALU]] -> Data
    memory -> [[Register File|register file]]
- We have two metrics for measuring performance: [[Latency|latency]] and
  [[Throughput|throughput]]
  - These are _not_ inverses of one another, because of concurrency!
  - We wish to minimize the overall time it takes to accomplish a set of `N`
    tasks
    - Specifically, [[CPU Time|CPU time]]
- We are also concerned with [[Power|power]] and [[Energy|energy]]
- "Iron Law" of Processor Performance: CPU Time = Instruction Count \* Cycles
  Per Instruction \* Cycle Time
  - Instruction count (IC): Size of the program
  - Cycles Per Instruction (CPI): Number of cycles per instruction
    ([[RISC-V|RISC]] vs. CISC)
  - Cycle Time (CT): Clock speed of processor
- One approach is to use [[Multi-Cycle Design|multiple cycles per instruction]]
