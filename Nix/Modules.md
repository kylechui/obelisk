---
id: "Modules"
aliases: []
tags:
  - "Nix"
---

- A module is an attribute set, or a function that returns an attribute set
  - If it is a function, then the function has the following default parameters:
    - `lib`: The `nixpkgs` function library
    - `config`: All configuration options of the current [[Flakes|flake]]
    - `options`: All options defined in all NixOS modules in the current
      [[Flakes|flake]]
    - `pkgs`: A collection of all packages in `nixpkgs`, as well as a set of
      functions related to packaging
    - If other arguments want to be passed in, use `specialArgs`
