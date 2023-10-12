---
id: "Linking"
aliases: []
tags:
  - "CSM151B"
---

- Linking is the process of saving the program counter somewhere, so the program
  knows where to "return" to after terminating
- This is commonly used as a "jump and link" pair, to implement function calls
  - For many consecutive function calls (e.g. recursion), we would continuously
    add the value of the program counter to the stack
