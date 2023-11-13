---
id: "Branch Predictor"
aliases: []
tags:
  - "CSM151B"
---

- The branch target buffer (BTB) stores target addresses
- Entries are indexed by PC
  - Map from PC -> target address
- When the instruction is decoded (and known to be a control-flow instruction,
  we can update the BTB)
- Only part of the PC is used for the BTB index, since otherwise the BTB would
  be massive
  - We then add a tag (the PC) and we can use that to check if we have seen an
    instruction recently (has not been overwritten)
    - We can optimize this by removing the BTB index, as well as the lowest two
      bits (always 0)
- We can also add one more bit for the branch history table (BHT), which
  remembers if the last time we saw this branch we got a "hit" or not (predicts
  same as last time anded with current hit)
  - For conditional branches update based on latest outcome of the branch (known
    at decode stage), otherwise set to 1
  - However, this does not react well to changes, and even for easy patterns we
    only get 80% accuracy
  - We could add a second bit to the BHT to have more information (bi-modal
    predictor), at the cost of more overhead
    - Only change the prediction if you see `00` or `11`
- To optimize returns and calls, we keep a stack of return addresses (return
  stack buffer or RSB)

## Do we get a benefit from using the BTB?

- If $r$-type/$i$-type/`lw`/`sw`, PC won't get matched in BTB
- If `jal`, then BTB works well
- If `beq`, then BTB works sometimes
- If `ret`/`call`/`jalr`, then BTB isn't very helpful since we could jump to
  many distinct locations
