---
id: Math 180 Lecture 8
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 9]]

- For a connected graph $G$, the following are equivalent:
  1. $G$ has an Eulerian walk (not necessarily closed)
  2. $G$ has either 0 or 2 vertices of odd degree
- **Proof**:
  - ($1 \Rightarrow 2$) Every vertex has even degree except for potentially the
    first and last vertices, for incoming/outgoing edges. If they are the same,
    then we have 0 vertices of odd degree, otherwise both have odd degree.
  - ($2 \Rightarrow 1$) If there are 0 vertices of odd degree, then we have an
    Eulerian cycle (from the previous Lemma). If there are 2 vertices of odd
    degree, we can add an extra edge between those two to create a graph with 0
    odd degree vertices, and so we get an Eulerian cycle again. Removing this
    edge, we get an Eulerian walk in the original graph.
- For a connected graph $G$, if all vertices have even degree, then
  - $G$ has one vertex, or
  - $G$ has a cycle
- **Proof**: Suppose $G$ has more than one vertex. Then we know that $G$ has at
  least one edge. However, to maintain even degree for all vertices (and finite
  graph size), we eventually have to return to one of the previous vertices,
  creating a cycle.
- A _Hamiltonian cycle_ in a connected graph $G$ is a cycle that visits every
  vertex exactly once.
- Let $G$ be a $m \times n$ grid. Then $G$ has a Hamiltonian cycle if and only
  if $m,n$ are not both even.
  - If we 2-color the vertices to be black and white, then we see that a
    Hamiltonian cycle exists if we have the same number of black and white
    vertices.
