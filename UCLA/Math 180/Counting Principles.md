---
id: Counting Principles
aliases: []
tags:
  - Math180
---

- Addition principle: If $A$ and $B$ are two disjoint sets, then
  $|A\cup B| = |A| + |B|$
  - More generally, if $A_1,\dotsc,A_n$ are disjoint sets, then
    $|A_1\cup\dotsb\cup A_n| = |A_1| + \dotsb + |A_n|$
- Multiplication principle: For all sets $A, B$, we have
  $|A\times B| = |A|\cdot |B|$
  - More generally, suppose $A$ is a set of objects such that every object in
    $A$ can be constructed in exactly one way by making a sequence of $k$
    choices. Suppose the the $i$th choice can be made in $n_i$ ways. Then
    $$
      |A| = \prod_{i=1}^k n_i
    $$
- Subtraction principle: If $A$ and $B$ are finite sets with $B\subset A$, then
  $|A\setminus B| = |A| - |B|$
- Division principle: TODO

## Helpful Facts/Definitions

- If $f\colon X\to Y$, and $f$ is a bijection, then $|X| = |Y|$
- The number of permutations of $n$ unique items is $n!$
