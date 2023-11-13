---
id: "Out of Order Execution"
aliases: []
tags:
  - "CSM151B"
---

- Instead of feeding the next instruction, we should feed the first available
  instruction
  - This causes new hazards (e.g. WAW and WAR)
  - Another issue is that if we do branch prediction incorrectly, some later
    instruction might finish completely before we realize the branch prediction
    was wrong (irrecoverable)
    - We avoid this by writing results to a temporary buffer in the "complete"
      stage, and only saving things for real in the "retire" stage
      - Also known as writing to the architectural stage
      - We must retire (or commit) in order
- We only are really doing the execution/completion stages out of order
- We retire in-order by utilizing a "re-order buffer" (ROB)
  - A circular table/buffer that holds completed instructions
  - Only retires an instruction if all preceding ones have been retired

## Hazards

- RAW: True dependence, no solution
- WAW/WAR: Output dependence, follow the order that the programmer intended
  - Can also use a different register to avoid race conditions, aka
    [[Register Renaming|register renaming]]

## Scheduling

- How can we figure out which instructions are "ready"?
- After decoding, we put instructions into a "reservation station"
- We replace the memory stage with functional units, which itself pipelines
  basic ALU operations
  - This then writes to the re-order buffer, which updates the
    [[Register Renaming|RAT]]

## Steps

- Fetch (can do multiple instructions simultaneously)
- Dispatch: Put instructions into reservation station
  - Also reserves an entry in the [[Register Renaming|ROB]]
  - If the ROB or RAT are full, stall
- Issue/Fire: Start execution once all sources are ready and the FU is available
  - Release the entry in the RS (but not ROB)
- Complete: Copy results into the ROB
  - Release the FU
  - Mark the destination register as ready
- Commit/Retire: Write the results to architectural state
  - If the instruction is the top of the ROB, commit it to memory
  - Mark the (old) physical register as free
