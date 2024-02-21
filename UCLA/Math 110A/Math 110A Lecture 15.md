---
id: Math 110A Lecture 15
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 16]]

- **Theorem**: Let $R$ be a commutative ring, with $I\subsetneq R$ a
  [[Maximal Ideal|maximal ideal]]. Then $I$ is [[Prime Ideal|prime]].
- **Proof**: Let $ab\in I$, for some $a, b\in R$. Without loss of generality,
  suppose $a\notin I$. Then $I + aR = R$, as $I$ is [[Maximal Ideal|maximal]].
  Thus there exists $i\in I$ and $r\in R$ such that $1_R = i + ar$. Then we have
  $$
  \begin{align*}
    b &= 1_Rb \\
      &= (i + ar)b \\
      &= ib + arb \\
      &= ib + (ab)r.
  \end{align*}
  $$
  Since $i, ab\in I$, we have $ib, (ab)r\in I$ as well. Therefore their sum is,
  and so we have $b\in I$, as desired.
- **Theorem**: Let $R$ be commutative, and $I\subsetneq R$ a proper
  [[Ideal|ideal]]. Then $I$ is [[Prime Ideal|prime]] if and only if $R/I$ is an
  [[Integral Domain|integral domain]].
- **Proof**:
  - ($\Rightarrow$) Suppose $I$ is [[Prime Ideal|prime]]. Take
    $a + I, b + I\in R / I$. Then if $(a + I)(b + I) = ab + I = 0_R + I$, so
    $ab\in I$. Since $I$ is [[Prime Ideal|prime]], we have $a\in I$ or $b\in I$.
    Therefore $a + I = 0_R + I$ or $b + I = 0_R + I$ and so $R/I$ is an
    [[Integral Domain|integral domain]].
  - ($\Leftarrow$) Take $ab\in I$. Then $(a + I)(b + I) = ab + I = 0_R + I$, so
    $a + I = 0_R + I$ or $b + I = 0_R + I$. Therefore $a\in I$ or $b\in I$, and
    so $I$ is [[Prime Ideal|prime]].
- **Theorem**: Let $R$ be commutative, and $I\subsetneq R$ a proper
  [[Ideal|ideal]]. Then $I$ is [[Maximal Ideal|maximal]] if and only if $R/I$ is
  a [[Field|field]].
- **Proof**:

  - ($\Rightarrow$) Suppose $I$ is [[Maximal Ideal|maximal]]. We wish to show
    that given some nonzero $a + I\in R / I$, there exists $b + I\in R / I$ such
    that $(a + I)(b + I) = ab + I = 1_R + I$. Since $a + I$ is nonzero, we know
    $a\notin I$. As $I$ is [[Maximal Ideal|maximal]], we have $I + aR = R$, so
    there exists $i\in I$ and $r\in R$ such that $1_R = i + ar$, or
    $ar\equiv 1_R\pmod I$. Therefore all nonzero elements in $R / I$ are
    [[Unit|units]], so $R / I$ is a [[Field|field]].

    Consider $r + I$. We have $(a + I)(r + I) = ar + I = 1_R + I$. Therefore
    $r + I$ serves as our multiplicative inverse to $a + I$, and so $R/I$ is a
    [[Field|field]].

  - ($\Leftarrow$) Suppose $R / I$ is a [[Field|field]]. Let $a\notin I$. Then
    $a\not\equiv 0_R\pmod I$, so $a + I$ is nonzero. Since $R / I$ is a field,
    there exists $b + I\in R / I$ such that $(a + I)(b + I) = ab + I = 1_R + I$.
    Thus there exists some $i\in I$ such that $ab + i = 1_R$. Therefore
    $1_R\in aR + I$. Since $1_R$ generates $R$, we have $aR + I = R$, so $I$ is
    [[Maximal Ideal|maximal]].
