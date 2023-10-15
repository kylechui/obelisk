---
id: "Derivations"
aliases: []
tags:
  - "Nix"
---

- A _derivation_ is a precise description of how contents of existing files are
  used to derive new files
  - This can be used for deriving a package's build artifacts, based on the
    dependencies that it requires
  - These build artifacts can then be used as inputs to another derivation
- This is the crux for how Nix manages dependencies!
