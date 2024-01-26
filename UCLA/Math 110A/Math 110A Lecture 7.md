---
id: Math 110A Lecture 7
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 8]]

- Let $R$ be a ring. Let $a\in \mathbb{R}$ be a [[Unit|unit]]. Then $a$ cannot
  be a [[Zero Divisor|zero divisor]].
- **Proof**: Suppose towards a contradiction that $a$ is a
  [[Zero Divisor|zero divisor]]. Then there exists $b\neq 0$ such that $ab = 0$.
  Since $a$ is a [[Unit|unit]], there exists $a^{-1}\in R$, so
  $$
    b = 1\cdot b = a^{-1}ab = a^{-1}0 = 0,
  $$
  a contradiction.
- Let $S\subseteq R$. $S$ is a [[Subring|subring]] if and only if $S$ satisfies:
  - $1\in S$
  - $S$ is closed under addition: $a,b\in S\implies a+b\in S$
  - $S$ is closed under multiplication: $a,b\in S\implies ab\in S$
  - $S$ is closed under additive inverses: $a\in S\implies -a\in S$
- If $S$ forms a [[Non-unital Rings|non-unital ring]] with the same conditions,
  or forms a ring with a different multiplicative identity, we say $S$ is a
  _non-unital subring_
- To show that $S$ is a [[Non-unital Rings|non-unital]] [[Subring|subring]], we
  need to show the last 3 conditions. Additionally, we need to show that
  $0\in S$ or $S\neq \varnothing$
- Let $R$ be an [[Integral Domain|integral domain]]. Let $a, b, c\in R$. Let
  $c\neq 0$. If $ac = bc$, then $a = b$.
- **Proof**: Suppose $ac - bc = 0$. Then $(a - b)c = 0$. Since $R$ is an
  [[Integral Domain|integral domain]], $a - b = 0$ or $c = 0$, so $a = b$.
- Every [[Field|field]] is an [[Integral Domain|integral domain]]
  - The converse isn't true; consider $R = \mathbb{Z}$
- **Proof**: Consider $a\in R$ such that $a\neq 0$. Then $a$ must be a
  [[Unit|unit]]. Therefore it cannot be a [[Zero Divisor|zero divisor]], so $R$
  must be an [[Integral Domain|integral domain]].
- **Theorem**: Every finite [[Integral Domain|integral domain]] is a
  [[Field|field]].
- **Proof**: Let $R = \{r_1,\dotsc,r_n\}$ be an
  [[Integral Domain|integral domain]]. Take $r_i\in R$ to be nonzero. Then
  $r_iR = \{r_ir_1,\dotsc,r_ir_n\}\subseteq R$. We wish to show that
  $|r_iR| = |R|$.

  Take $r_ir_j, r_ir_k\in r_iR$. Suppose that $r_ir_j = r_ir_k$. Then
  $r_i(r_j - r_k) = 0$. Since $R$ is an [[Integral Domain|integral domain]], we
  know that $r_i = 0$ or $r_j - r_k = 0$. Therefore $r_j = r_k$. Therefore we
  have an injection from $R$ to $r_iR$, so $|R|\leq |r_iR|$. Therefore
  $|R| = |r_iR|$, and so $r_iR = R$. Since $1\in R$, we know that there exists
  some $r_j$ such that $r_ir_j = 1$, so $r_i$ is a [[Unit|unit]]. Therefore $R$
  must be a [[Field|field]].
