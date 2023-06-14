---
id: "Advanced Register Allocation"
aliases:
  - "Chordal Graphs"
tags:
  - "CS132"
---

## Chordal Graphs

- A chordal graph is an undirected graph where:
  - The nodes are program variables
  - The edges are overlapping "live ranges"
  - Every 4-cycle contains a _chord_, which is an edge between two non-adjacent
    nodes in the cycle
- We have that interval graphs are a subset of chordal graphs, which are a
  subset of perfect interference graphs
  - All interference graphs are perfect, but 95% are chordal as well
    - Coloring perfect interference graphs is NP-complete
    - Coloring chordal interference graphs can be done in polynomial time

## Method 1: Greedy Coloring

- Iterate through the graph in some order, and color the graph greedily using
  such that no two neighbors have the same color

## Simplicial Elimination Ordering

- This is a way to order the nodes in a chordal interference graph
- A node $v$ is _simplicial_ if its neighborhood is a clique
- The simplicial elimination order of a graph is an ordering $v_1,\dotsc,v_n$
  such that for all $i$, $v_1,\dotsc,v_i$ is a simplicial subgraph
  - For a chordal graph and SEO, greedy coloring is optimal
- One idea to make graphs chordal is to rename the same variable into multiple
  names based on the control flow of the program
  - This is called static single assignment (SSA) form
- A program is _strict_ if for all variables, the variable is assigned to before
  use
- Every strict program in SSA form has a chordal interference graph
  - We can convert the last 5% _in polynomial time_!
  - All modern compilers transform to SSA, which is useful for other
    optimizations
