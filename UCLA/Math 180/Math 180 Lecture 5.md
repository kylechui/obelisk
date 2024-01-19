---
id: Math 180 Lecture 5
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 6]]

- [[Graph Isomorphism]] is an equivalence relation
- The number of [[Simple Graph|simple graphs]] with $n$ vertices is
  $2^{\binom{n}{2}}$, because we take the power set of $\binom{n}{2}$ edges
- The number of graphs in an equivalence class is upper-bounded $n!$ because we
  can permute the vertices
  - Therefore the number of non-[[Isomorphic Graph|isomorphic]] simple graphs
    with $n$ vertices is lower-bounded by $2^{\binom{n}{2}} / n!$
- We define a relation on $V$ such that $u\sim v$ if there exists a
  [[Walk|walk]] from $u$ to $v$
  - It is an equivalence relation, and we call the classes connected components
  - If there is only one connected component, the graph is called _connected_
