---
id: Math 180 Lecture 10
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 11]]

- A vertex $v$ is a _leaf_ or _end-vertex_ of a graph $G$ if it has degree 1
- **Leaf Lemma**: Every tree with $\geq 2$ vertices contains at least two leaves
- **Proof**: Let $P = (v_0, e_1, v_1, \dotsc, e_t, v_t)$ be a path of maximal
  length in $G$. Since $G$ is connected and $G$ has $\geq 2$ vertices, it has at
  least one edge. Therefore the length of $P$ is $\geq 1$, and $v_0\neq v_t$.

  We claim that $v_0$ and $v_t$ are leaves. If $v_0$ is not a leaf, then there
  are at least two edges incident to $v_0$. Therefore there exists some edge
  $e = \{v_0, v\}$ different from $\{v_0, v_1\}$ incident to $v_0$. If $v$ is
  already in the path, then $P$ with $e$ forms a cycle, contradicting that $G$
  is a tree. If $v$ is not a vertex in $P$, then we can increase the length of
  $P$ by adding $e$, contradicting maximality of $P$.

- **Tree-growing Lemma**: Let $G$ be a graph and $v$ a leaf of $G$. The
  following are equivalent:
  1. $G$ is a tree.
  2. $G\sm v$ is a tree.
- **Proof**: (1 $\Rightarrow$ 2) Let $G$ be a tree, and $x, y$ vertices of
  $G\sm v$. Since $G$ is connected, there is a path in $G$ from $x$ to $y$.
  Since the path only (potentially) has degree 1 vertices at its endpoints, we
  know that $v$ must not be on this path. Hence the path is contained in
  $G - v$, and as this holds for all $x, y$, we know $G - v$ is connected. Any
  cycle in $G - v$ must also be a cycle in $G$, so we know $G - v$ is a tree.

  (2 $\Rightarrow$ 1) Suppose $G - v$ is a tree. Since any cycle contains only
  vertices of degree $\geq 2$, we may add $v$ anywhere without introducing a
  cycle. Let $u$ be the vertex incident to $v$ in $G$. Since $G - v$ is
  connected, $u$ is connected to every other vertex of $G - v$ by a path. Since
  $\{u, v\}$ is an edge, $G$ is connected.
