---
id: Math 180 Lecture 9
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 10]]

- A graph is _$k$-connected_ if $|V| \geq k + 1$ and it remains connected after
  removing any $k - 1$ vertices.
  - For example, $K_n$ is $n - 1$-connected
- Let $G$ be a graph
  - For all $e\in E$, we denote the graph with $e$ missing by $G - e$
  - For all $v\in V$, we denote the graph with $v$ (and all edges incident to
    $v$) missing by $G - v$
  - $G + e$ is adding a duplicate edge to the graph
  - $G \% e$ is subdividing an edge
- $G'$ is a _subdivision_ of $G$ if we can get to $G'$ from $G$ by repeatedly
  subdividing edges
- $G$ is 2-connected if and only if for all $u, v\in V$, there is a cycle
  containing $u$ and $v$
- **Proof**:

  - ($\Rightarrow$) Suppose $G$ is 2-connected. Let $u, v$ in $V$. We induct on
    the length of the shortest path from $u$ to $v$. In our base case let
    $d_G(v, v') = 1$, so they are adjacent. Since $G$ is 2-connected, we know
    that $G\setminus e$ must be connected, since there must exist a path from
    $v$ to $v'$ that doesn't go through $e$. Therefore there must be a cycle
    through $v$ and $v'$.

    For the inductive step, we assume there exists a cycle containing $u$ and
    $v$, for all $u, v$ such that $d_G(u, v) < k$. Consider two vertices
    $v_0, v_k$ such that $d_G(v_0, v_k) = k$. By the induction hypothesis, there
    exists a cycle that includes $v_0, v_{k - 1}$, or two distinct paths from
    $v_0$ to $v_{k - 1}$. Since $G$ is 2-connected, $G\setminus v_{k - 1}$ is
    connected, so there is a path from $v_0$ to $v_k$ in $G\setminus v_{k - 1}$.
    This path, combined with the natural path from $v_0$ to $v_k$, forms a cycle
    including the two.

  - ($\Leftarrow$) Suppose $u, v\in V$, with a cycle containing them. If we
    remove a vertex, we can still get from $u$ to $v$ by going through one of
    the two paths from $u$ to $v$.

- $G$ is 2-connected if and only if every sub-division of $G$ is 2-connected
- If $G$ is 2-connected, then $G + e$ is 2-connected
  - You're only adding an edge, so this should only _improve_ the connectivity
    of the graph
