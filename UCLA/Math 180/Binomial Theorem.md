---
id: Binomial Theorem
aliases: []
tags:
  - Math180
---

- **Theorem**: For all $n \geq 0$, we have
  $$
  (x + y)^n = \sum_{k = 0}^n \binom{n}{k}x^ky^{n - k}.
  $$
  - **Proof**: If we expand the left-hand side, we have a product of $n$ terms,
    each being $x + y$. In order to get a term that contains $x^ky^{n - k}$
    (since for every term we choose either an $x$ or a $y$), we need to choose
    $k$ $x$s from $n$ total terms. There are $\binom{n}{k}$ ways to do this, and
    we sum over all possible values of $k$.
