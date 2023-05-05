---
id: "Linear Scan Register Allocation"
aliases:
  - "Steps"
tags:
  - "CS132"
---

## Steps

1. Scan the program from left to right
2. The live range of a variable is a single interval
3. Order the variables after where they are first assigned
4. Process the live ranges from left to right (greedily)
5. Every decision of $v\mapsto r$ is tentative until made permanent or the
   variable is put into memory
6. Spilling is based on "how far the interval extends into the future"
