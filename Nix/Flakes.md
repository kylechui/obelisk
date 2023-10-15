---
id: "Flakes"
aliases: []
tags:
  - "Nix"
---



- Nix flakes allow you to declaratively manage packages and configuration as
  functions
  - This allows one to create reproducible development environments
  - Flakes also create `flake.lock` files, which pin packages to specific commit
    hashes, further improving reproducibility
    - Before, we would need to use `fetchTarball` and manually set which version
      of `nixpkgs` we wanted to use

## Flake Syntax

- Initialize a flake using `nix flake init`
- Run a flake using `nix develop .#FLAKE_NAME`
- Update the flake's inputs using `nix flake update`
  - This will update the lockfile, which contains the upstream dependencies

## Example Flake

- The below flake can be run using `nix develop .#myFlake`

```nix
{
  description = "A very basic flake that prints hello world";
  outputs = { self, nixpkgs }:
    let
      system = "x86_64-linux";
      pkgs = nixpkgs.legacyPackages.${system};
      flakeName = "myFlake";
    in {
      ${flakeName} = pkgs.mkShell {
        shellHook = ''
          echo "hello world"
        '';
      };
    };
}
```


