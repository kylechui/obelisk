---
id: Memory Management
aliases: []
tags:
  - CSM151B
---

- Programs should have their memory isolated from one another in memory
- Each program typically has different regions: code, data, heap, stack, etc.
- Some code can be _shared_ among multiple programs
- A portion of the memory is reserved for OS and other privileged systems
- Memory management is controlled by the OS or system software or hardware
- Shared code/libraries (e.g. standard libraries, drivers, etc.) can access
  read-only shared memory spaces
  - Operating system is just another program
- Some desirable properties for our memory management:
  - Protection: Each program should not be able to affect the others
    - Implement bounds checking
  - Location-independence: Program might be moved anywhere in memory
    - Use a base pointer (base + offset addressing)
- One way to manage memory is to statically partition it
  - But this makes us unable to add new programs
  - We also can't adjust the amount of space a program gets allocated
- Another way is to only partially partition the memory
  - Divide the memory into fixed-size blocks (pages)
  - We expose [[Virtual Addresses|virtual addresses]] to the programs
  - Use a [[Page Table|page table]] to map virtual addresses to physical
    addresses
