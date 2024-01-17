---
id: Math 180 Lecture 4
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 5]]

## Examples of [[Graph|Graphs]]

- Path graphs: $P_n$
  - $V = \{0, 1, \dotsc, n\}$
  - $\varphi(e_i) = \{i, i + 1\}$ for $i < n$
- Cycle graphs: $C_n$
  - $V = \{0, 1, \dotsc, n\}$
  - $\varphi(e_i) = \{i, i + 1\}$ for $i < n$
  - $\varphi(e_n) = \{n, 0\}$
- Complete graphs: $K_n$
  - $V = \{0, 1, \dotsc, n\}$
  - $\varphi(e_i) = \{i, j\}$ for $i, j < n$ and $i < j$
- Complete bipartite graphs: $K_{m, n}$
  - $V = \{0, 1, \dotsc, m + n\}$
  - $\varphi(e_i) = \{i, j\}$ for $i < m$ and $j \geq m$

## More definitions

- A _path_ in $G$ is a [[Subgraph|subgraph]] of $G$ that is a path graph
- A _cycle_ in $G$ is a [[Subgraph|subgraph]] of $G$ that is a cycle graph
