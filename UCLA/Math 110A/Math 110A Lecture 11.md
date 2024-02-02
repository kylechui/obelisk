---
id: Math 110A Lecture 11
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 12]]

- Let $R$ be a ring and $I\subseteq R$ an [[Ideal|ideal]]. If $R$ is
  commutative, then so is $R / I$.
- **Proof**: Take $a + I, b + I\in R / I$. Then we have
  $$
  (a + I)(b + I) = ab + I = ba + I = (b + I)(a + I).
  $$
- This is not true, consider $I = R$. Then $R / I = \{0\}$ which is clearly
  commutative, even if $R$ may not be.

## Examples

- Consider $R = \mathbb{Z}$ and $I = (n)$. Then $R / I = \mathbb{Z} / n$
- Let $R = F[x, y]$, where $F$ is a [[Field|field]]. If we consider
  $I = (x, y)$, then $R / I\cong F$. Given some $p\in F[x, y]$, we can write
  $$
    p = \sum_{i \geq 0}\sum_{j \geq 0} a_{ij}x^iy^j.
  $$
  All of the non-constant terms are congruent to $0\pmod I$, so we are left with
  the coefficients $a_{ij}\in F$.

## [[Canonical Projection]]

- Let $R$ be a ring and $I\subseteq R$ an [[Ideal|ideal]]. The
  [[Canonical Projection|canonical projection]] $\pi\colon R\to R / I$ is a
  surjective [[Ring Homomorphism|ring homomorphism]] with $\ker(\pi) = I$.
- **Proof**: Take $a + I\in R / I$. Then $\pi(a) = a + I$. In fact, any
  $b\in a + I$ maps to $a + I$. Thus $\pi$ is surjective. We now show the ring
  homomorphism properties:

  - $\pi(a + b) = a + b + I = (a + I) + (b + I) = \pi(a) + \pi(b)$
  - $\pi(ab) = ab + I = (a + I)(b + I) = \pi(a)\pi(b)$
  - $\pi(1_R) = 1_R + I = 1_{R / I}$
    - Note that for all $a\in R$, we have $(1_R + I)(a + I) = a + I$, and
      similarly for right-identity.

  It remains to be shown that $\ker(\pi) = I$.

  - Suppose we have some $a\in\ker(\pi)$. Then $a + I = \pi(a) = 0_R + I$. Thus
    $a\equiv 0\pmod I$, so $a\in I$. Therefore $\ker(\pi)\subseteq I$.
  - Given some $a\in I$, we know that $a\equiv 0\pmod I$. Then we have
    $\pi(a) = a + I = 0_R + I$. Thus $a\in\ker(\pi)$ and so
    $I\subseteq\ker(\pi)$.
