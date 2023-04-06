---
id: "Top-down Parsing"
aliases:
  - "Nullable"
tags:
  - "CS132"
---

- At a node $A$, select a production $A\to \alpha$ and construct the appropriate
  child for each symbol of $\alpha$
  - We will impose extra restrictions on top of non-ambiguity to guarantee that
    we will make a good choice of $\alpha$
    - Some choices of $\alpha$ could result in a non-terminating parser!
    - In particular, top-down parsers can't handle left-recursive grammars
- Backtrack if a terminal is added that doesn't match the input string
  - This can incur significant performance penalties
- Find the next node to be expanded (must have a label in $V_n$)

## Nullable

- For a string $\alpha$ of grammar symbols, define $\mathrm{NULLABLE}(\alpha)$
  as $\alpha$ can go to $\varepsilon$.
- For each production, something is nullable if all of its components are
  nullable

## First

- For a string $\alpha$ of grammar symbols, define $\mathrm{FIRST}(\alpha)$ as
  the set of all terminal symbols $a$ such that $\alpha$ can produce a string
  that starts with $a$
  - If our parser has disjoint $\mathrm{FIRST}$ sets for each of the productions
    for the current symbol, we don't need to backtrack

## Follow

- For a non-terminal $B$, define $\mathrm{FOLLOW}(B)$ as the set of terminals
  that can appear immediately to the right of $B$
