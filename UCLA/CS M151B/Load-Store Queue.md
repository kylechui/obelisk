---
id: Load-Store Queue
aliases: []
tags:
  - CSM151B
---

- The idea is that we have something similar to the ROB but for store
  instructions
- We assign an entry in the decode stage, and store values in the queue once the
  instruction has completed
- We only _truly_ write to memory if the instruction has been retired
- Also known as LSQ
