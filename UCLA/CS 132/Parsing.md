---
id: "Parsing"
aliases:
  - "Top-down vs. Bottom-up Parsing"
tags:
  - "CS132"
---

- A context-free syntax is specified using a context-free grammar (CFG)
  - It is identified by the 4-tuple $(V_t, V_n, S, P)$:
    - $V_t$ is the set of terminal symbols (tokens returned by the scanner)
    - $V_n$ is the set of non-terminal symbols (sets of strings occurring in the
      language that impose structure)
    - $S$ is the set of all strings in the language
    - $P$ is the set of productions specifying how strings are formed in the
      language
- Grammars are often written in Backus-Naur form (BNF)
  - Non-terminals are written with angle brackets or capital letters
  - Terminals are written using `typewriter` font or <ins>underlined</ins>
- To perform a derivation, we choose a non-terminal to replace at every step
  - We can replace the left-most or right-most non-terminal
- The order can affect what syntax tree is generated, which influences the
  implied order of evaluation
  - By introducing intermediate levels in the grammar, we can force a certain
    derivation for an input string (i.e. force the correct tree to be generated)
    and avoid [[Ambiguity|ambiguity]]
  - A separate step will handle ambiguities, not parsing

## Top-down vs. Bottom-up Parsing

- [[Top-down Parsing|Top-down parsers]]
  - Start at the root and fill in
  - May require backtracking
    - Some grammars don't require backtracking, i.e. they are
      [[Predictive Parsing|predictive]]
    - Can be mitigated by looking ahead a few tokens
- Bottom-up parsers
  - Start at leaves and fill it in
  - Start in a state valid for legal first tokens
  - As input is consumed, change state to encode possibilities
  - Use a stack to store both state and sentential forms
