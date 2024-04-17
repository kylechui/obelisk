---
id: Math 180 Lecture 15
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 16]]

- A _(proper) vertex coloring_ of a graph is an assignment of _colors_ to its
  vertices such that the colors of any two adjacent vertices are distinct.
  Without loss of generality, we can assume that our graphs are simple.
- A graph is called _$k$-colorable_ if its vertices can be properly colored
  using $\leq k$ colors. A 2-colorable graph is called _bipartite_.
  - The cube is the only Platonic solid whose skeleton is bipartite.
  - Petersen's graph is 3-colorable but not 2-colorable.
- Every planar graph is 4-colorable.
- Every planar graph is 5-colorable.
- **Proof 1**: We first show that any planar graph has a vertex of degree
  $\leq 5$. If $|V| < 3$, this is clearly true, so let $|V| \geq 3$. Suppose
  towards a contradiction that there exists no vertex with degree $\leq 5$. Then
  every vertex must have degree $\geq 6$, so $2|E| \geq 6|V|$ and
  $|E| \geq 3|V|$. Since $|V| \geq 3$, we have $|E| \leq 3|V| - 6$, a
  contradiction.

  Now we proceed via induction on $|V|$. If $|V| < 5$, then this is trivial. Let
  $v$ be a vertex of degree $\leq 5$. If $\deg(v)\leq 4$, then by the induction
  hypothesis, $G\setminus v$ has a 5-coloring and we can color $v$ using the
  color not used by its (at most) 4 neighbors. Thus it suffices to show the
  statement is true when $\deg(v) = 5$.

  Let $t, u, z, x, y$ denote the vertices in clockwise cyclic order incident to
  $v$. If they do not use up all 5 colors, then we may color $v$ using one of
  the remaining colors. Hence we may assume that the colors of all the vertices
  are distinct. Consider $x, y$ and let

  $$
  V_{x, y}\coloneqq \{u\in V(G\setminus v)\mid c(u)\in \{c(x), c(y)\}\}
  $$

  denote the set of vertices with the same color as $x$ or $y$. Then we have two
  cases:

  1. There is no path in $G\setminus v$ only using vertices in $V_{x, y}$ from
     $x$ to $y$. Let $V_{x, y}'$ denote the set of vertices reachable from $x$
     via only vertices in $V_{x, y}$. Then $x\in V_{x, y}'$ and
     $y\notin V_{x, y}'$.

  2. There is a path $P$ in $G\setminus v$ only using vertices in $V_{x, y}$
     from $x$ to $y$. Consider $z, t$. Since $P\cup \{\{v, x\}, \{v, y\}\}$ is a
     cycle with $z$ and $t$ on opposite sides, any path from $z$ to $t$ in
     $G\setminus v$ must intersect $P$, so there is no path in $G\setminus v$
     only using vertices in $V_{z, t}$ from $z$ to $t$. Then we are in case 1,
     and we are done.
