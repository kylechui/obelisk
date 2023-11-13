---
id: "Flushing"
aliases: []
tags:
  - "CSM151B"
---

- The process of clearing incorrectly-fetched instructions
- The hazard detection unit sends signals indicating when to flush
- We replace all three of the incorrectly-fetched instructions with bubble (or
  no-op) instructions
  - This is the same as stalling for three cycles
- We can reduce the miss penalty by resolving the branch sooner, i.e. at the
  decode stage
  - If we add some comparator that compares `rs1` and `rs2` during the decode
    stage, then we would know whether or not we are branching
  - This makes the penalty for "missing" just one cycle instead of three
    - Our CPI becomes roughly 1.14
