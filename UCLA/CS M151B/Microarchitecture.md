---
id: "Microarchitecture"
aliases: []
tags:
  - "CSM151B"
---

- A microarchitecture is just the hardware implementation for the interface that
  an [[Instruction Set Architecture|ISA]] provides
- A given [[Instruction Set Architecture|ISA]] can have multiple
  microarchitectures implementing its operations
  - The goal for a good microarchitecture is to have both fast performance and
    low power draw
- Every microarchitecture has two parts
  - [[Datapath]]: A collection of functional units that process the data/create
    the data-flow
  - [[Controller]]: The unit that directs operation/activities on the datapath
    (e.g. which operands to load)
