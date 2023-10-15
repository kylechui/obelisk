---
id: "Nix Store"
aliases: []
tags:
  - "Nix"
---

- The Nix store is where components are stored, usually in `/nix/store`
  - All components are stored in _isolation_; all have unique names
  - Uniqueness is provided via a cryptographic hash of all inputs involved in
    building the component
    - Prevents interference between components
    - Allows for complete identification of dependencies
      - This prevents duplication of identical components
- The full path of a directory entry in the Nix store is called the store path
- The hash is computed recursively, since any changes in the dependencies must
  be propagated to the root program's hash
- Upgrading is always done by rebuilding the component in question, never
  destructively
- During deployment, we find the transitive closure of our component under the
  "depends on" relation, and deploy all of it to the target machine
