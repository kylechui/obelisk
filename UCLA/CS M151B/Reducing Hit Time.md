---
id: Reducing Hit Time
aliases: []
tags:
  - CSM151B
---

- Use direct map (or set-associative to balance between direct map and fully
  associative)
- Use smaller cache in the lower levels
- Parallel lookup
  - Access tags and data simultaneously
  - Access each way simultaneously
- Speculative load: Instead of waiting for a store, issue the load speculatively
  - Causes a lot of issues
