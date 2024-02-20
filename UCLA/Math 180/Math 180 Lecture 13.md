---
id: Math 180 Lecture 13
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 14]]

- The codes generated by unlabeled planted trees are in a bijection with ballot
  sequences
- Typically, we plant all trees with shortest subtrees to the left.
- For a vertex $v$, define its excentricity to be
  $$
  \mathrm{ex}(v) = \max \{d(u, v)\mid u\in V\}.
  $$
- The _center_ of $G$ is
  $C(G) = \{v\in V\mid \mathrm{ex}(v)\text{ is minimal}\}$.
- For any tree $T$, $C(T)$ has at most two vertices. If $C(T)$ has two vertices
  $x$ and $y$, then $\{x, y\}$ must be an edge in $T$.
- **Proof**: Let $T = (V, E)$ be a tree. If $T$ has $\leq 2$ vertices, then its
  center is $V$. If not, then it has at least 2 leaves. Not all of the vertices
  of $T$ are leaves, so $T'$ (the tree obtained by removing all leaves) is
  non-empty. Then for all vertices $v\in V$, we have
  $\mathrm{ex}_{T'}(v) = \mathrm{ex}_T(v) - 1$, so $C(T) = C(T')$. Repeating
  this process until $T'$ has less than or equal to 2 vertices yields the
  desired result. If $T'$ ends up with two vertices, then they are connected by
  an edge, as desired.
- If $C(T)$ is a single vertex $v$, define the code to be the code of $(T, v)$.
  If $C(T)$ consists of two vertices $x$ and $y$, then consider the two subtrees
  $T_x, T_y$ of $T\sm \{x, y\}$. Let $A, B$ denote the codes of $T_x, T_y$
  respectively. Let $x$ be the root if $A \leq B$ in lexicographic order,
  otherwise $y$.
  - This results in trees having shorter paths to the left.

## Planar Graphs

- A graph is _planar_ if it can be drawn (embedded) in the plane (or
  equivalently the sphere) so that its edges do not intersect
- Let $U\subseteq \mathbb{R}^2$. We define an equivalence relation on $U$ by
  $x\sim y$ if there is a continuous path from $x$ to $y$.
- We call the connected components of the complement of a planar drawing the
  _faces_ of the graph.
  - Note that the "outside" of the graph is also an _outer face_. It makes more
    sense to consider it a face if you use stereographic projection to project
    the graph onto a sphere.
- For any graph $G$, we have $|V| - |E| = b_0 - b_1 = \chi(G)$ as the _Euler
  characteristic_ of $G$.
- The number of faces of an embedded planar graph $G$ is $|F| = b_1 + 1$. In
  particular, $|F|$ does not depend on a planar embedding of $G$.
- **Proof**: If we keep removing edges until we get a forest, we merge faces and
  remove edges at the same time. For a forest, we have $b_1 = 0$ and exactly one
  face (the outer face). We have removed exactly $b_1$ edges.
- For any planar graph, we have $|V| - |E| + |F| = b_0 + 1$. In particular for
  any connected planar graph, we have $|V| - |E| + |F| = 2$.
- **Proof**: This follows from $|V| - |E| = b_0 - b_1$ and $|F| = b_1 + 1$.
- The _degree_ of a face is the number of edges on its boundary.
- We have $2|E| = \sum_{f\in F}\deg(f)$.
- **Proof**: Use the same double-counting argument that we used for degrees of
  vertices and edges.

## Non-Planar Graphs

- $K_5$ is not planar.
- **Proof**: Suppose towards a contradiction that $K_5$ is planar. Then by
  Euler's formula, we have $|F| = 7$. However since each face has at least 3
  sides, we have $|E| \geq 7\cdot 3 / 2$, a contradiction.
- $K_{3, 3}$ is not planar.
- **Proof**: Suppose towards a contradiction that $K_{3, 3}$ is planar. Then by
  Euler's formula, we have $|F| = 5$. However since each face has at least 4
  sides (since $K_{3, 3}$ is bipartite), we have $|E| \geq 5\cdot 4 / 2$, a
  contradiction.