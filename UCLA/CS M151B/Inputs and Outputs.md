---
id: Inputs and Outputs
aliases: []
tags:
  - CSM151B
---

- Aside from the processor and [[Memory|memory]], we have other components
  commonly referred to as Input/Outputs or I/Os
- Some categories of devices include:
  - Storage (flash/disk/tape)
  - Network (Ethernet/WiFi/Bluetooth/LTE)
  - Human-machine interfaces (keyboard/mouse/touchscreen/video)
  - Printers (line/laser/inkjet/photo)
  - Actuators (valves/robots/car brakes)
- How do we read/write to I/Os?
  - One way is to dedicate a set of registers for reading/writing, or have a
    dedicated channel of communication
  - Another is memory-mapped I/O
    - Map a reserved part of the memory to I/O
    - Communication becomes loads/stores to that section of memory
    - Usually no need to cache since it is constantly changing
  - We use [[IO Bus|I/O buses]]
  - Since memory-mapped I/O is slow, we can try direct memory access (DMA)
    - A unit that sits between the I/O bus and the memory, to help offload some
      memory-related tasks from the CPU
    - We can communicate the presence of data to the CPU using an interrupt, or
      have the CPU continuously poll the DMA
      - Polling has CPU overhead and can be difficult to implement, but can be
        fully scheduled
      - Interrupts are easier to do and more efficient, but can interrupt the
        CPU at bad times
    - Exception: Unusual runtime condition
    - Trap: Transfer of control synchronously to a handler when an exception
      occurs
    - Interrupt: External event that occurs asynchronously to the current thread
      - Interrupt exception occurs, and the CPU experiences a trap
