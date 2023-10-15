---
id: "Reproducible Scripts"
aliases: []
tags:
  - "Nix"
---

- When we write our own shell scripts, we often rely on custom dependencies
- We would like to guarantee that our target machine always contains these
  dependencies
  - This can be done by including shebang commands to install the packages from
    `nixpkgs`
