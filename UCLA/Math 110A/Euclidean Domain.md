---
id: Euclidean Domain
aliases: []
tags:
  - Math110A
---

- Let $R$ be an [[Integral Domain|integral domain]]. A _norm_ is a non-negative
  function $N\colon R\to \mathbb{Z}$ such that

  - $N(0_R) = 0$
  - Given $a, b\in R$ with $b\neq 0_R$, there exist $q, r\in R$ such that
    $a = bq + r$ and either $r = 0_R$ or $N(r) < N(b)$

  A _Euclidean Domain_ is an [[Integral Domain|integral domain]] $R$ with a norm
  $N$.
