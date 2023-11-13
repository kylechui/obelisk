---
id: "Superscalar"
aliases: []
tags:
  - "CSM151B"
---

- A "scalar" pipeline is where we are only ever processing one data at a time
  - Thus the IPC is _at most_ 1 (really less, since stalls + hazards)
  - Therefore we can only improve cycle time (limited by technology)
- We can process multiple instructions at the same time via instruction-level
  parallelism (ILP)

## Instruction-level Parallelism

- A pipelined processor that can process multiple instructions simultaneously is
  called "super scalar"
- The general idea is to try and double "everything", e.g. fetch two
  instructions at once
  - Forwarding doesn't work if the instructions are issued at the same time
    - Checking for these dependencies increases quadratically with the number of
      instructions you try to execute in parallel (check each destination
      register with the inputs of all other instructions)
    - We can increase our speed via
      [[Out of Order Execution|out of order execution]]
