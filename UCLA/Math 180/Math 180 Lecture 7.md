---
id: Math 180 Lecture 7
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 8]]

- **Theorem**: Let $D = (d_1,\dotsc,d_n)$ such that
  $0 \leq d_1 \leq \dotsb \leq d_n \leq n - 1$. We create a new sequence
  $D' = (d_1', \dotsc, d_{n - 1}')$ defined by
  $$
  d_i' = \begin{cases}
    d_i & \text{if }i < n - d_n \\
    d_i - 1 & \text{otherwise}
  \end{cases}
  $$
  $D$ is a degree sequence if and only if $D'$ is a degree sequence.
- **Proof**:
  - ($\Rightarrow$) Suppose $D$ is a degree sequence. We don't necessarily have
    that the last vertex is connected to the previous $d_n$ vertices. We know
    that there exists a graph $G$ with $D$ as its degree sequence. Suppose there
    is a vertex in $\{v_{n - d_n},\dotsc,v_{n - 1}\}$ that is not connected to
    $v_n$. Let $v_j$ be the right-most such vertex. Then since $v_n$ has degree
    $d_n$, there must exist some $v_k$ with $k < n - d_n \leq j$ connected to
    $v_n$. Since the degrees are in weakly-increasing order, we have
    $d_k \leq d_j$. Since $v_k$ is adjacent to $v_n$ (and $v_j$ is not), there
    exists some vertex that is connected to $v_j$ that is not connected to
    $v_k$, call it $v_\ell$. Then we have the two edges $\{v_\ell, v_j\}$ and
    $\{v_k, v_n\}$. By swapping the edges to be $\{v_j, v_n\}$ and
    $\{v_\ell, v_k\}$, we preserve the degree of each vertex, while connected
    $v_j$ to $v_n$. Repeating this enough times will connect $v_n$ to each of
    its $d_n$ "previous" neighbors, and so removing it will yield a valid degree
    sequence.
  - ($\Leftarrow$) Suppose $D'$ is a degree sequence. We can create a graph out
    of it. To get a graph for $D$, we add a new vertex and have an edge connect
    to each of the last $d_n$ vertices in the original graph.
- Eulerian walk: A closed walk in a graph $G$ that uses every edge exactly once
- For a connected graph $G$, the following are equivalent:
  - $G$ has a closed Eulerian walk
  - All vertices of $G$ have even degree
- **Proof**:

  - ($1\Rightarrow 2$) Taking the closed Eulerian walk, we trace out $G$. For
    every vertex, we need an edge to get to that vertex, and a different edge to
    leave, so the degree of each vertex must be even.
  - ($2\Rightarrow 1$) Suppose all vertices have even degree. We say a _tour_ is
    a walk that does not repeat edges. Let $T$ be a maximal (i.e. longest) tour.
    We wish to show that $T$ is a closed Eulerian walk $e_1,\dotsc,e_m$.

    - We know that $v_0 = v_m$, otherwise $T$ would not be maximal.
    - Let $V(T) = \{\text{vertices in }T\}$. We wish to show $V(T) = V$. If
      there existed some $v_k\notin V(T)$, then there exists some vertex
      $v\in V(T)$ such that $\{v, v_k\}\in E$ (otherwise $G$ would be
      disconnected). Then $T$ would not be a maximal tour, so
