---
id: "Diamond Problem"
aliases: []
tags:
  - "Nix"
---

- Consider a package `Base` that requires two dependencies, `A` and `B`
  - If `A` and `B` require differing versions of a single dependency (e.g. `Cv1`
    and `Cv2`), then we have an issue
