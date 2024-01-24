---
id: Math 180 Lecture 6
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 7]]

- The _distance_ between vertices in a graph is a function
  $d_G\colon V\times V\to \mathbb{Z}$ such that
  $$
    d_G(x, y) = \min \{k\mid \text{there exists a path of length $k$ from $x$ to $y$}\}
  $$
- Suppose $G$ is a simple graph with vertices $[n]$. The _adjacency matrix_ of
  $G$ is the $n\times n$ matrix defined by
  $$
    A_{ij} = \begin{cases}
      1 & \text{if $\{i,j\}\in E(G)$} \\
      0 & \text{otherwise}
    \end{cases}
  $$
- The $(i, j)$-entry of $A^k$ is the number of paths of length $k$ from $i$ to
  $j$.
  - We use the notation $Z_{ij}^k$
- Let $v_1,\dotsc,v_n$ be the vertices $G$. Then the sequence
  $\deg(v_1), \deg(v_2),\dotsc,\deg(v_n)$ arranged in weakly increasing order is
  called the _degree sequence_ or _score_ of $G$
- Handshake Lemma: For any graph $G$, $\sum_{v\in V}\deg(v) = 2|E|$
  - Each edge is counted in the degree of each of its two endpoints
