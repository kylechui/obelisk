---
id: Math 180 Lecture 17
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 18]]

- Let $G$ be a 4-cycle, with $e$ an edge. Then:
  - $G - e$ is a tree, so $p_{G - e}(k) = k(k - 1)^3$.
  - $G / e$ is just $K_3$, so $p_{G / e}(k) = k(k - 1)(k - 2)$
  - $p_G(k) = p_{G - e}(k) - p_{G / e}(k) = k(k - 1)(k^2 - 3k + 3)$
- If $G$ is an edgeless graph on $n$ vertices, then $p_{G}(k) = k^n$.
- **Proof**: Each of the vertices can be any of the $k$ colors, since we don't
  have to worry any neighbors sharing a color.
- Note that this (with the deletion-contraction formula) provides an
  exponential-time algorithm for computing $p_G(k)$ for any graph.
- The chromatic polynomial is a polynomial in $k$.
- **Proof**: Induct on the number of edges in $G$, and use the
  deletion-contraction formula as an inductive step.
- The chromatic polynomial $p_G(k)$ is monic, of degree $n = |V|$.
- **Proof**: We need to show that $p_G(k)\sim k^n$ as $k\to\infty$. Note that
  $p_G(k) / k^n$ is the probability that a random assignment of colors results
  in a valid coloring. For large $k$, almost all colorings are proper.

  Alternatively, we can induct on the number of edges. If $|E| = 0$, then
  $p_G(k) = k^n$, and the statement holds. If it holds for all graphs with
  $\leq m - 1$ edges, then knowing $G - e$ and $G / e$ have $\leq m - 1$ edges,
  we have $p_{G}(k) = p_{G - e}(k) + p_{G / e}(k)\approx k^n$.

## Acyclic Orientations

- An _acyclic orientation_ of graph $G$ is a directed graph obtained by
  orienting the edges of $G$ without creating an oriented cycle. Let
  $\mathrm{ao}(G)$ denote the number of such orientations.
