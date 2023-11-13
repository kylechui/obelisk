---
id: "Hazards"
aliases: []
tags:
  - "CSM151B"
---

- A situation in [[Pipeline Design|pipelining]] where we can't execute properly
  - There are three kinds: Data, Control, and Structural

## Data Hazards

- Read after Write (RAW)
  - If we read before write finishes, then we yield the wrong output
- Other similar issues are WAW, WAR, RAR
  - RAR is never an issue because we always reading the same thing
  - WAW is not an issue because instructions are run in order, and the latter
    instruction will take precedence
    - Also called _output dependency_
  - WAR is not an issue because the decode stage always happens way before the
    write stage, so the read will always happen first
    - Also called _false dependency_

### Solutions to RAW

- Stop the processor until the first instruction reaches the write back stage
  - Replace normal instructions with "bubble" (no-op) instructions
  - This is called "stalling"
- Use results from the previous stage immediately without storing in
  intermediate register
  - Requires extra connections in the [[Datapath|datapath]]
  - Also known as "forwarding" or "bypassing"
  - We usually forward from register to register
    - ALU result -> ALU source
    - Memory -> ALU source (Load-Use Data Hazard)
      - Need to stall once, so we can forward from the beginning of memory into
        the ALU

## Forwarding Detection

- The forwarding unit detects hazards and issues control signals that signify to
  other pieces of the circuit when to bypass
  - It will also signal to the instruction registers to do nothing, even if the
    positive edge of the clock arrives
  - We have a RAW Hazard and forward from `EX/MEM` pipeline register when:
    - EX/MEM `rd` = ID/EX `rs1` or EX/MEM `rd` = ID/EX `rs2`
    - EX/MEM `RegWrite` = 1
  - We have a RAW Hazard and forward from `MEM/WB` pipeline register when:
    - MEM/WB `rd` = ID/EX `rs1` or MEM/WB `rd` = ID/EX `rs2`
    - MEM/WB `RegWrite` = 1
  - We have a Load-Use Hazard when:
    - ID/EX `rd` = IF/ID `rs1` or ID/EX `rd` = IF/ID `rs2`
    - ID/EX `MemRead` = 1
    - Have to stall for one cycle

## Structural Hazards

- One unit is busy and cannot be used for another instruction
  - Happens when we share resources
  - Doesn't occur for our design (since there is no sharing)

## Control Hazards

- When the flow of instruction addresses is not known nor expected
- Stalling: How many cycles should we stall for? How can we detect when to
  stall?
  - Three W's
    - When does the branch occur?
      - Known after decode stage
    - Where do we branch to?
      - End of the execution stage (after ALU computes PC + offset)
    - Whether or not to branch?
      - Known after the memory stage
- We can try stalling until we know the outcome of the branch
  - However this is too slow; another approach is to use
    [[Speculation|speculation]]
