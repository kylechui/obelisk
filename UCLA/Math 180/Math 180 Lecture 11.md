---
id: Math 180 Lecture 11
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 12]]

- If $G = (V, E)$ is a tree, then $|V| - |E| = 1$.
- **Proof**: We induct on the number of vertices. It is trivially true when
  $|V| = 1$. For any larger graph, every time we add a vertex we are adding an
  edge as well, which preserves our invariant.
- The number of connected components in $G$ is called the _zeroth Betti number_
  of $G$, and is denoted by $b_0 = b_0(G)$. The first Betti number
  $b_1 =
  b_1(G)$ is the maximal number of edges whose removal does not change
  the number of connected components in $G$.
  - **Note**: It's not clear that these values are independent of edge removal
    order
- A graph $G = (V, E)$ is a forest if and only if $b_1 = 0$. Then
  $b_0 = |V| - |E|$ and $b_1 = 0$.
- **Proof**: ($\Rightarrow$) Let $G$ be a forest, and suppose towards a
  contradiction that $b_1\neq 0$. Then there is an edge that can be removed
  without increasing $b_0$. If $G_i$ is the component containing $e = \{u, v\}$,
  then $G_i - e$ is connected, so there are two paths from $u$ to $v$ in $G_i$,
  i.e. a cycle. Thus we have a contradiction.

  ($\Leftarrow$) Let $b_1 = 0$. Suppose towards a contradiction that $G$ is not
  a forest. Then there must exist a cycle in $G$, otherwise removing some edge
  $e$ would increase $b_0$. Let $e = \{u, v\}$ be an edge in the cycle $C$. If
  we remove $e$, then we do not change the number of connected components of
  $G$, since any path that required the edge from $u$ to $v$ can now use the
  other path from $u$ to $v$ (necessitated by the cycle). If we look at the
  $b_0$ connected components, each has $|V| - |E| = 1$, so in total our graph
  has $|V| - |E| = b_0$.

- **Theorem**: For any graph $G = (V, E)$, we have
  $$
    |V| - |E| = b_0 - b_1.
  $$
  We call this value $\chi(G)$ or the _Euler characteristic_ of $G$.
- **Proof**: Let us keep removing edges in cycles until we get a forest. Both
  $|V|$ and $b_0$ are invariant under this process. Therefore this forest has
  $|V| - b_0$ edges. Hence we removed $|E| - |V| + b_0$ edges, so
  $b_1 = |E| - |V| + b_0$. This also shows that $b_1$ is well-defined, since we
  made no assumptions about the edge removal order.
- Any three of the following properties of a graph $G$ imply the fourth:
  1. $G$ is connected
  2. $G$ is acyclic
  3. $G$ has $n$ vertices
  4. $G$ has $n - 1$ edges
- **Proof**: Each of the properties can be described via the following:
  1. Connected: $b_0 = 1$
  2. Acyclic: $b_1 = 0$
  3. $n$ vertices: $|V| = n$
  4. $n - 1$ edges: $|E| = n - 1$
