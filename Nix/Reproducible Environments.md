---
id: "Reproducible Environments"
aliases: []
tags:
  - "Nix"
---

- With a declarative shell environment, we can:
  - Automatically set environment variables
  - Execute shell commands at instantiation
  - Share the shell with other developers
    - Could be yourself in the future, e.g. after you pass a class you uninstall
      all the relevant packages, but putting them into an environment would
      allow you to re-install and run your old code at will
  - Version control the developer environment
