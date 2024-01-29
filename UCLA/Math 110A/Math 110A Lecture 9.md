---
id: Math 110A Lecture 9
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 10]]

- The kernel of any [[Ring Homomorphism|ring homomorphism]] is an
  [[Ideal|ideal]]
  - In fact, all [[Ideal|ideals]] can be realized as the kernel of some
    [[Ring Homomorphism|ring homomorphism]]
- Every [[Principal Ideal|principal ideal]] is an [[Ideal|ideal]]
- **Proof**: Let $R$ be a commutative ring, with $a\in R$. We first show that it
  is a non-unital subring:
  - $(a)$ is non-empty because $a = a\cdot 1\in (a)$
  - $(a)$ is closed under addition because $ar_1 + ar_2 = a(r_1 + r_2)\in (a)$
  - $(a)$ is closed under multiplication because
    $ar_1\cdot ar_2 = a(ar_1r_2)\in (a)$
  - $(a)$ is closed under additive inverses because $-(ar_1) = a(-r_1)\in (a)$
  - $ar\in (a), x\in R$. Then $arx = a(rx)\in (a)$
- Examples of [[Ideal|ideals]]
  - Let $R$ be a ring. Then $(0) = \{0\}$ and $(1) = R$ are [[Ideal|ideals]].
  - Consider $\mathbb{Z}$. Let $n\in \mathbb{Z}$ be positive. Then $n\mathbb{Z}$
    is an [[Ideal|ideal]].
  - Let $S$ be a set and $R$ a ring. Let $T\subseteq S$. Then
    $\mathcal F(S, R) = \{\text{all functions from } S\to R\}$ is a ring
  - Consider $A_T = \{f\in \mathcal F(S, R)\mid f(x) = 0\text{ for }x\in T\}$.
    Then $A_T$ is an [[Ideal|ideal]].
