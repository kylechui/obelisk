---
id: Math 180 Lecture 14
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 15]]

- The _dual graph_ $G^* = (V^*, E^*, \varphi^*)$ is the graph with
  $V^*\coloneqq F$, $E^*\coloneqq \{e^*\mid e\in E\}$, and
  $\varphi^*(e^*)\coloneqq \{F_i, F_j\}$ if $e$ is on the common boundary of
  $F_i, F_j$.
- If $G = (V, E)$ is a connected planar graph and $|V| \geq 3$, then
  $|E| \leq 3|V| - 6$.
- **Proof**: Suppose a face has degree 1 or 2. In the former, we have a loop. In
  the latter, we have a non-simple graph or a non-closed face, a contradiction.
  Hence every face must have degree at least 3. Thus $3|F|\leq 2|E|$. Plugging
  this into Euler's formula yields the desired result.

## Regular Convex Polyhedra

- Suppose we have a convex polyhedron where:
  - Every vertex has degree $d$
  - Every face has degree $k$
- Then we have

  $$
  \begin{gather*}
    d|V| = 2|E| = k|F| \\
    |V| + |F| = |E| + 2 \\
    \frac{2}{d}|E| + \frac{2}{k}|E| = |E| + 2 \\
    \frac{1}{d} + \frac{1}{k} = \frac{1}{2} + \frac{1}{|E|} > \frac{1}{2}
  \end{gather*}
  $$

  Since $d \geq 3$ and $k \geq 3$, the only possible pairs $(d, k)$ are:

  $$
    (3, 3), (3, 4), (4, 3), (3, 5), (5, 3).
  $$

  These are the five platonic solids:

  | $d$ | $k$ | polyhedron   | $\|V\|$ | $\|E\|$ | $\|F\|$ |
  | --- | --- | ------------ | ------- | ------- | ------- |
  | 3   | 3   | tetrahedron  | 4       | 6       | 4       |
  | 3   | 4   | cube         | 8       | 12      | 6       |
  | 4   | 3   | octahedron   | 6       | 12      | 8       |
  | 3   | 5   | dodecahedron | 20      | 30      | 12      |
  | 5   | 3   | icosahedron  | 12      | 30      | 20      |
