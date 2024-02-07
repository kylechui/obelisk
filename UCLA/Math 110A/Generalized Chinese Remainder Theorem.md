---
id: Generalized Chinese Remainder Theorem
aliases: []
tags:
  - Math110A
---

- Let $R$ be a ring. Let $I, J\subseteq R$ be [[Ideal|ideals]] such that
  $I + J = R$. Then for any $a, b\in R$, we can find $x\in R$ such that
  $x\equiv a\pmod I$ and $x\equiv b\pmod J$. Moreover, if $y$ is another
  solution satisfying the previous two equivalencies, then
  $y\equiv x\pmod{I\cap J}$.
- **Proof**: Take $a, b\in R$. Since $I + J = R$, we can express $1 = i + j$ for
  for some $i\in I$ and $j\in J$. Observe that $i + j\equiv i\pmod J$ and
  $i + j\equiv j\pmod I$, so $i\equiv 1\pmod J$ and $j\equiv 1\pmod I$. Let
  $x = ib + ja$. Then we have $x\equiv ib\pmod J$, so $x\equiv b\pmod J$.
  Similarly, $x\equiv ja\pmod I$, so $x\equiv a\pmod I$.

  If $y$ is another solution, then $y\equiv x\pmod I$ and $y\equiv x\pmod J$.
  Hence $y - x\in I$ and $y - x\in J$, so $y - x\in I\cap J$. Therefore
  $y\equiv x\pmod{I\cap J}$, as desired.
