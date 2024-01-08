---
id: Division Algorithm
aliases: []
tags:
  - Math110A
---

- Let $a, b\in \mathbb Z$, such that $b > 0$. Then there exists unique
  $q, r\in \mathbb Z$ such that $a = bq + r$, where $0 \leq r < b$.
- **Proof**: Let $a, b\in \mathbb{Z}$, with $b > 0$. Consider the set
  $S = \left\{a - bx\mid x\in \mathbb{Z}\right\}\cap \mathbb{Z}_{\geq 0}$.

  We first show that $S$ is non-empty. If we pick
  $x = -\left\lvert a\right\rvert$, then we have

  $$
    a - b(- \left\lvert a\right\rvert)=  a + b \left\lvert a\right\rvert\geq 0,
  $$

  so $S\neq\varnothing$.

  By the [[Well-Ordering Principle]], we know that $S$ must have a minimum
  element. We denote this minimal element as $r$. We know that $r\geq 0$, since
  $r\in S\implies r\in \mathbb{Z}_{\geq 0}$. Furthermore, let the corresponding
  $x$ be denoted by $q$.

  Suppose towards a contradiction that $r \geq b$. Then, $r - b\geq 0$.
  Furthermore, we can write $r - b = a - b(x + 1)$. Therefore $r - b\in S$,
  contradicting $r$'s minimal element property. Thus we have
  $0 \leq r < b, q\in \mathbb{Z}$ satisfying $a = bq + r$.

  Finally, we show uniqueness. Suppose $q, q', r, r'\in\mathbb{Z}$ such that
  $a = bq + r$, $a = bq' + r'$, and $0 \leq r, r' < b$. Then

  $$
  \begin{align*}
    bq + r &= bq' + r' \\
    b(q - q') &= r' - r.
  \end{align*}
  $$

  Since $0\leq r, r' < b$, and $b\mid (r' - r)$, we have $r - r' = 0$, so
  $r = r'$. Thus $b(q - q') = 0$, so $q = q'$.
