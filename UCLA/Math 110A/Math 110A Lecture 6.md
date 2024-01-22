---
id: Math 110A Lecture 6
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 7]]

- Some examples of [[Ring|rings]]:
  - $\{0\}$
  - $\mathbb{Z}$
  - $\mathbb{Z}_n$ (for $n\neq 0$)
  - For [[Ring|rings]] $R, S$, we have $R\times S$ is also a [[Ring|ring]] (the
    operations defined element-wise)
- Some non-examples of [[Ring|rings]]:
  - $M_{n\times n}(\mathbb{R})$ (multiplication is non-commutative)
- Given a [[Ring|ring]] $R$, we define
  $R[x] = \{a_0 + a_1x + a_2x^2 + \dotsb + a_nx^n\mid a_i\in R, n\in \mathbb{Z}_{\geq 0}\}$
- $R[x]$ is [[Commutative Ring|commutative]] if and only if $R$ is
  [[Commutative Ring|commutative]]
- When there are multiple [[Ring|rings]], we denote the additive identity by
  $0_R$ and the multiplicative identity by $1_R$
  - If there is no ambiguity, we drop the subscripts
- If $\gcd(a, n) > 1$, then $[a]$ is a [[Zero Divisor|zero divisor]] for
  $\mathbb{Z}_n$
- If $\gcd(a, n) = 1$, then $[a]$ is a [[Unit|unit]] for $\mathbb{Z}_n$
- Let $R$ be a [[Ring|ring]]. Let $a, b, c\in R$. The following are true:
  - The additive identity is unique
    - $0 = 0 + 0' = 0'$
  - The additive inverse is unique
    - $b = 0 + b = b' + a + b = b' + 0 = b'$
    - Left-cancellation for addition: $a + b = a + c$ implies $a = c$
      - Add $-a$ to both sides
  - The multiplicative identity is unique
  - If $a$ is a [[Unit|unit]], its multiplicative inverse is unique
  - $0\cdot a = a\cdot 0 = 0$
    - $0 \cdot a = (0 + 0)\cdot a = 0\cdot a + 0\cdot a$, left-cancel
  - $a\cdot (-b) = (-a)\cdot b = -a\cdot b$
  - $-(-a) = a$
  - $-(a + b) = -a - b$
  - $-(a - b) = -a + b$
  - $(-a)(-b) = ab$
