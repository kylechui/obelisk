---
id: "Von-Neumann Machine"
aliases: []
tags:
  - "CSM151B"
---

- We assume that we have some sort of linear memory model, where we can access
  both data and instructions
- A program is specified as a list of instructions and they are executed
- The machine is a kind of [[Finite State Machine|finite state machine]]
  - A program counter identifies the current instruction
  - Each instruction maps the current state of the machine to a new state
