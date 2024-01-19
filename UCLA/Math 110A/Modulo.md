---
id: Modulo
aliases: []
tags:
  - Math110A
---

- Let $a, b, n \in \mathbb{Z}$, and $n \geq 0$. We say that $a, b$ are
  _congruent modulo_ $n$, if $n$ divides $a - b$
  - It is written as $a\equiv b\pmod n$, and it means that $n\mid a - b$
- Congruence $\mod n$ is an equivalence relation

  - Reflexivity: Given $a \in \mathbb{Z}$, we have $a \equiv a \mod n$, since
    $n\mid a - a$
  - Symmetry: Let $a, b\in \mathbb{Z}$. If $a\equiv b\pmod n$, then
    $n\mid a - b$. Note that $n\mid b - a$ as well, so $b\equiv a\pmod n$
  - Transitivity: Let $a, b, c \in \mathbb{Z}$. Suppose $a\equiv b\mod n$ and
    $b\equiv c\mod n$. Since $n\mid a - b$ and $n\mid b - c$, then there exists
    $k_1, k_2\in \mathbb{Z}$ such that $nk_1 = a - b$ and $nk_2 = b - c$. Adding
    these together yields $n(k_1 + k_2) = a - c$, so $n\mid a - c$ and
    $a\equiv c\pmod n$
