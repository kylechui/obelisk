---
id: Math 110A Lecture 16
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 17]]

## Polynomials Over [[Field|Fields]]

- Let $F$ be a [[Field|field]]. Recall, that given $f\in F[x]$, we can uniquely
  express
  $$
    f = \sum_{i = 0}^N a_i x^i,
  $$
  where $N \geq 0$ and $a_i\in F$.
- Let $f, g\in F[x]$. The following hold:
  1. $\deg(f + g) \leq \max(\deg(f), \deg(g))$.
  2. $\deg(fg) = \deg(f) + \deg(g)$.
- The [[Unit|units]] in $F[x]$ are the nonzero constant polynomials, i.e. the
  embedding of $F$ itself into $F[x]$.
- **Theorem**: Let $f, g\in F[x]$ such that $g\neq 0$. There are unique
  polynomials $q, r\in F[x]$ such that $f = g\cdot q + r$, where
  $\deg(r) < \deg(g)$.
- **Proof**: Consider the set $S = \{f - s\cdot g\mid s\in F[x]\}$. We choose
  the element of $S$ that has the lowest [[Polynomial Degree|degree]], call it
  $f - s\cdot g$. Let $r = f - s\cdot g$, with $q = s$. Then we clearly have
  $f = g\cdot q + r$. It suffices to show that $\deg(r) < \deg(g)$.

  Suppose towards a contradiction that $\deg(r)\geq \deg(g)$. Let

  $$
    \begin{gather*}
    r = a_nx^n + \dotsb + a_0 \\
    g = b_mx^m + \dotsb + b_0.
    \end{gather*}
  $$

  Since $\deg(r)\geq \deg(g)$, we have $n\geq m$. Then
  $r - (\frac{a_n}{b_m}x^{n - m})g$ has a lower degree than $r$, since the $x^n$
  term has been "canceled out". Note that this polynomial is still in $S$. This
  contradicts that $r$ has the lowest [[Polynomial Degree|degree]] in $S$, and
  so we have $\deg(r) < \deg(g)$.
