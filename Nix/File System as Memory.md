---
id: "File System as Memory"
aliases: []
tags:
  - "Nix"
---

- Many [[Software Deployment Issues|issues with managing deployments]] can be
  thought about from the perspective of memory management of programming
  languages
  - Managing [[Nix Store|the store]] is just a different level in the memory
    hierarchy
- Store paths are analogous to memory addresses
  - The string representing a path is analogous to a pointer, and accessing a
    file is equivalent to a pointer dereference
  - String manipulation for paths is analogous to pointer arithmetic
- From this lens, component interference is just an address collision problem
- Dangling pointers are dangerous, as they can lead to referencing an absent
  component
- We use conservative garbage collection to manage the store, e.g. anything that
  looks like a path is considered a path, and is included in our component
