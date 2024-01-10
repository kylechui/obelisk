---
id: Bezout Identity
aliases: []
tags:
  - Math110A
---

- Let $a, b\in \mathbb{Z}$, not both zero. Suppose $d = \gcd(a, b)$. Then there
  exists $r, s\in \mathbb{Z}$ such that $ar + bs = d$
- **Proof**: Consider
  $S = \left\{am + bn\mid m, n\in \mathbb{Z}\right\}\cap \mathbb{Z}_{>0}$. We
  first show that $S$ is non-empty. Consider $m = a, n = b$. Then
  $am + bn = a^2 + b^2 > 0$, as $a, b\neq 0$.

  Hence by the [[Well-Ordering Principle]], $S$ has a minimum element; call it
  $d = am + bn$. We now show that $d = \gcd(a, b)$. By the
  [[Division Algorithm]], we can write $a = dq + r$, so

  $$
  \begin{align*}
    r &= a - dq \\
      &= a - (am + bn)q \\
      &= a - amq - bnq \\
      &= a(1 - mq) + b(-nq)
  \end{align*}
  $$

  Since $r \geq 0$, we have two cases:

  - If $r > 0$, then $r\in S$, and $d \leq r$ (since $d$ is the minimum element
    of $S$). However, by [[Division Algorithm]], $r < d$, a contradiction.
  - Hence $r = 0$, so $a = dq$ and $d\mid a$.

  By a similar argument, one can show that $d\mid b$.

  Finally, we show that if $c > 0$, $c\mid a$, and $c\mid b$, then $c \leq d$.
  Let $x, y\in \mathbb{Z}$ such that $a = cx$ and $b = cy$. Then

  $$
  \begin{align*}
    d &= am + bn \\
      &= (cx)m + cy(n) \\
      &= c(xm + yn)
  \end{align*},
  $$

  so $c\mid d$. Therefore $d = \gcd(a, b)$.
