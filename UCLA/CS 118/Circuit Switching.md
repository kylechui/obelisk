---
id: "Circuit Switching"
aliases: []
tags:
  - "CS118"
---

- Resources needed along a path (buffers, link bandwidth) are _reserved_ for the
  duration of the session
  - The sender can transfer the data to the receiver at a _guaranteed, constant
    rate_
- Implemented with either frequency division multiplexing or time-division
  multiplexing
  - FDM shares the frequency spectrum among its connections (bandwidth)
  - TDM segments the time domain into slots, and then assigns each connection a
    slice of time
- It can be wasteful because the circuits are idle during "silent periods"
