---
id: "Category of Sets"
aliases: []
tags:
  - "BasicCategoryTheoryforComputerScientists"
---

- The [[Categories|category]] of sets is often denoted $\mathbf{Set}$
  - The objects are sets
  - The morphisms are total functions between sets
  - Composition is defined $(g\circ f)(a) = g(f(a))$, satisfying the associative
    property
  - The identity function is defined $id(x) = x$ for any set
- Note that a function can correspond to multiple arrows in $\mathbf{Set}$
  - For example, $f(x) = x^2$ can be from $\mathbb R\to \mathbb R$ or
    $\mathbb R\to \mathbb R^{\geq 0}$
