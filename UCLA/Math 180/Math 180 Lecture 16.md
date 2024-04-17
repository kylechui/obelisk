---
id: Math 180 Lecture 16
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 17]]

- Another way to view a coloring is an assignment of colors to vertices via
  $c\colon V\to [k]$ where $c(u)\neq c(v)$ if $\{u, v\}\in E$.
- The _chromatic number_ $\chi(G)$ of a graph is the minimal number of colors
  needed to color a graph.
  - There exists no efficient algorithm to compute the chromatic number of a
    graph.
- For example, $\chi(K_n) = n$ and $\chi(C_n)$ is $2$ if $n$ is even, $3$
  otherwise.
- The _clique number_ $\omega(G)$ is the size of the largest [[Clique|clique]]
  in $G$.
- For all graphs $G$, we have $\chi(G)\geq \omega(G)$.
- **Proof**: If we observe the subgraph of $G$ isomorphic to $K_{\omega(G)}$,
  then we cannot color that with any less than $\omega(G)$ colors.
- An _independent set_ is a (sub)set of vertices such that no two of them share
  an edge.
  - The size of the largest independent set is given by $\alpha(G)$.
- $\chi(G)\geq |V|/\alpha(G)$
- **Proof**: Let $c$ be a coloring using $\chi(G)$ colors. For all
  $i\in \{1,\dotsc,\chi(G)\}$, let $V_i\coloneqq \{v\in V\mid c(v) = i\}$. Then
  we have that each $V_i$ is an independent set.
- $\chi(G)\leq \max_{v\in V} \deg(v) + 1$.
- **Proof**: If this weren't true, then we could not color the $v$ having the
  maximal degree.
- The _chromatic polynomial_ for a graph $G$ is defined by
  $$
    p_G(k) = \text{the number of $k$-colorings of }G.
  $$
- For example, $p_{K_n}(k) = k(k - 1)\dotsb(k - n + 1)$.
  - We also have $p_{C_4} = k(k - 1)^2 + k(k - 1)(k - 2)^2$.
- Deletion-contraction formula: $p_G(k) = p_{G - e}(k) - p_{G / e}(k)$
  - Contracting an edge is just merging the two end vertices of the edge into
    one vertex, and all associated edges
  - We get this formula by splitting into cases where the (former) endpoints of
    $e$
