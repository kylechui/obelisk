---
id: "Morphisms"
aliases: []
tags:
  - "BasicCategoryTheoryforComputerScientists"
---

- A monomorphism is an arrow $f\colon B\to C$ such that for all arrows
  $g, h\colon A\to B$, we have $f\circ g = f\circ h\implies g = h$
  - In $\mathbf{Set}$, these are just functions such that
    $f(x) = f(y)\implies x = y$
- An epimorphism is an arrow $f\colon A\to B$ such that for all arrows
  $g, h\colon B\to C$, we have $g\circ f = h\circ f\implies g = h$
  - In $\mathbf{Set}$, these are just functions such that for all $b\in B$,
    there exists $a\in A$ such that $f(a) = B$
