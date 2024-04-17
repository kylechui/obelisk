---
id: Field of Fractions
aliases: []
tags:
  - Math110A
---

- **Idea**: We can construct $\mathbb{Q}$ from $\mathbb{Z}$ by identifying pairs
  $(a, b)$ such that $a, b\in \mathbb{Z}, b\neq 0$ with the rational
  $\frac{a}{b}$.
- Let $R$ be an [[Integral Domain|integral domain]]. We define
  $S(R)\coloneqq \{(a, b)\mid a, b\in R, b\neq 0_R\}$.

  We define an equivalence relation on $S$ by $(a, b)\sim (a', b')$ if
  $ab' = a'b$. Then we define the operations of addition and multiplication by:

  - $(a, b) + (c, d) = (ad + bc, bd)$
  - $(a, b)\cdot (c, d) = (ac, bd)$

  The _field of fractions_ of $R$ is then defined as
  $\mathrm{Frac}(R)\coloneqq S(R) / \sim$, with the above operations.
