---
id: "Logic Design"
aliases: []
tags:
  - "CSM151B"
---

- To implement a [[Microarchitecture|microarchitecture]], we have to use
  sequential and combinational hardware elements
  - Combinational: Operates on data, output is a function of input
  - Sequential (State): Stores information
    - Elements are stored when the clock signal is 1
    - We use the positive edge to trigger this (when we flip from 0 → 1)
    - There is some propagation delay in updating the value in [[Memory|memory]]
    - Some registers are _write-enabled_, and we need both the write signal and
      clock to be 1 to successfully update the register
