---
id: Math 110A Lecture 13
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 14]]

- [[Generalized Chinese Remainder Theorem]]
- **Theorem**: Let $R$ be a ring, with $I, J\subseteq R$ [[Ideal|ideals]].
  Suppose $I + J = R$. Then we have the following isomorphism:
  $(R / I)\times (R / J)\cong R / (I\cap J)$.
- **Proof**: This relies heavily on the [[First Isomorphism Theorem]], and so we
  try to define $I\cap J$ as the kernel as some map $f$. Consider
  $f\colon R\to R / I \times R / J$, where $f(a) = (a + I, a + J)$. Note that
  this map is a [[Ring Homomorphism|homomorphism]], because:

  - It satisfies addition:
    $$
    \begin{align*}
      f(a + b) &= (a + b + I, a + b + J) \\
      &= (a + I, a + J) + (b + I, b + J) \\
      &= f(a) + f(b).
    \end{align*}
    $$
  - It satisfies multiplication:
    $$
    \begin{align*}
      f(ab) &= (ab + I, ab + J) \\
      &= (a + I, a + J)(b + I, b + J) \\
      &= f(a)f(b).
    \end{align*}
    $$
  - It maps identity to identity:
    $f(1_{R}) = (1 + I, 1 + J) = 1_{R / I \times R / J}$.

  We claim that $\ker(f) = I\cap J$.

  - Take $a\in I\cap J$. Then
    $$
    \begin{align*}
      f(a) &= (a + I, a + J) \\
      &= (0 + I, 0 + J) \\
      &= 0_{R / I \times R / J}.
    \end{align*}
    $$
    Thus $a\in \ker(f)$, so $I\cap J\subseteq \ker(f)$.
  - Conversely, take $a\in\ker(f)$. Then we know that
    $f(a) = 0_{R / I \times R / J} = (0 + I, 0 + J)$. However, we also have by
    definition that $f(a) = (a + I, a + J)$, so $a\in I$ and $a\in J$. Therefore
    $a\in I\cap J$ and $\ker(f)\subseteq I\cap J$, as desired.

  By the [[Generalized Chinese Remainder Theorem]], since $I + J = R$, we have
  that for all $x, y\in R$, we can find some $a\in R$ such that
  $a\equiv x\pmod I$ and $a\equiv y\pmod J$. In other words, for all $x, y$,
  there exists some $a$ such that $f(a) = (x + I, y + J)$. Therefore $f$ is
  surjective.

  By the [[First Isomorphism Theorem]], we have that
  $R / \ker(f)\cong \mathrm{Im}(f)$, so $R / (I\cap J)\cong R / I \times R / J$,
  as desired.
