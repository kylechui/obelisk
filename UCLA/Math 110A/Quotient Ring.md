---
id: Quotient Ring
aliases: []
tags:
  - Math110A
---

- Let $R$ be a ring, $a, b\in R$, and $I\subseteq R$ an [[Ideal|ideal]]. The
  _quotient ring_ $R / I$ is the set of congruence classes modulo $I$ with
  addition and multiplication defined by:
  - $(a + I) + (b + I) = (a + b) + I$
  - $(a + I)(b + I) = ab + I$
- The general motivation is to generalize the construction of $\mathbb{Z} / n$
  from $\mathbb{Z}$ to general rings
- Given an ideal $I\subseteq R$, we can define an equivalence relation $a\sim b$
  if $a - b\in I$. We can then "inherit" addition and multiplication from $R$.
  Given equivalence classes $[a]$ and $[b]$, we define $[a + b] = [a] + [b]$ and
  $[ab] = [a][b]$
- Let $R$ be a ring. Let $a, b\in R$ and $I\subseteq R$ be an ideal. We say $a$
  and $b$ are congruent modulo $I$ if $a - b\in I$. We denote the congruence
  class containing $a$ by $a + I$. When $a, b$ are congruent modulo $I$, we
  write $a\equiv b\pmod I$ or $a + I = b + I$.
