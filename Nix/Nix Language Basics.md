---
id: "Nix Language Basics"
aliases: []
tags:
  - "Nix"
---

- The Nix language is designed for creating and composing
  [[Derivations|derivations]]
- Nix is lazy, dynamically typed, purely functional
- Whitespace is used for delimiting lexical tokens, and is otherwise
  insignificant
- Values in the Nix language are primitives, lists, attribute sets, or functions
  - Attribute sets are basically just JSON blobs
  - Multi-line strings have equal amounts of prepended whitespace removed
  - Recursive attribute sets allow one to access attributes from within the set
  ```nix
  rec {
    one = 1;
    two = one + 1;
    three = two + 1;
  }
  ```
  - The `with` keyword is similar to OCaml's `scope.(op1 op2 ...)`
  - The `inherit` keyword is similar to JavaScript's object structuring, e.g.
  ```nix
  {
    inherit x y; # Same as { x = x; y = y; }
  }
  ```

## `builtins`

- `import` just evaluates some file and returns the result
- `builtins.fetch*`
  - All of these download something to the [[Nix Store|Nix store]] and return
    the path
