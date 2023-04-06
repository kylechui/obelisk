---
id: "LL Parsing"
aliases: []
tags:
  - "CS132"
---

- The first 'L' stands for "left-to-right" reading of the input
- The second 'L' stands for "left-most derivation"
- It is a type of [[Top-down Parsing|top-down parsing]]
- The main idea is that for each possible production ($\varepsilon$ or not), the
  next character in our string is unique, so we have an unambiguous way to
  derive the expression
- Some provable facts:
  - No left-recursive grammar is LL(1)
  - No ambiguous grammar is LL(1)
  - Some languages have no LL(1) grammar
  - If the grammar satisfies the unique $\mathrm{FIRST}$ condition and is
    $\varepsilon$-free, then it is a simple LL(1) grammar
