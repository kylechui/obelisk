---
id: Math 180 Lecture 12
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 13]]

## Classifying Trees

- Given two trees, how can we tell if they are [[Graph Isomorphism|isomorphic]]
  or not?
- Rooted Tree: A _rooted tree_ is a pair $(T, r)$ where $T$ is a tree and $r$ is
  a distinguished vertex called the _root_.
  - By convention, we draw the root at the top and everything else below.
  - If $\{x, y\}$ is an edge such that $y$ is on the path from $x$ to $r$, then
    we say that $y$ is the "parent" of $x$ and $x$ is the "child" of $y$.
- Planted Tree: A rooted tree $(T, n)$ along with a planar drawing. It can be
  identified with a triplet $(T, r, (v_v)_{v\in V})$ where $v_v$ is a linear
  ordering of the children of $v$.
- Two rooted trees $(T, r)$ and $(T', r')$ are isomorphic if there is an
  isomorphism that sends $T\mapsto T'$ and $r\mapsto r'$.
- Two planted trees $(T, r, v_v)$ and $(T, r', (v'))$ are isomorphic if they are
  isomorphic as rooted trees and the isomorphism preserves the ordering of the
  children.
- We can encode a planted tree as a binary string, with 1s indicating a step
  away from the root, and 0s indicating a step towards the root.
- **Theorem**: Let the code for planted tree be $a_1, \dotsc, a_m$. Then
  $m = 2n$ where $n = |V| - 1$, and $a_1 + \dotsb + a_k \geq 0$.
- **Proof**: Every edge is taken exactly twice. The sum is just the distance to
  the root, so it must be non-negative. The number of planted trees with $n + 1$
  vertices is the number of ballot sequences of length $2n$, or the number of
  Catalan numbers.
