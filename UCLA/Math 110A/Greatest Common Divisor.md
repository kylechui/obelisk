---
id: Greatest Common Divisor
aliases: []
tags:
  - Math110A
---

- Let $a, b\in \mathbb{Z}$ with $a$ and $b$ not both 0. The _greatest common
  divisor_ of $a$ and $b$ is the largest integer dividing $a$ and $b$
  - $\gcd(a, b)\mid a$ and $\gcd(a, b)\mid b$
  - For all $c > 0$ such that $c\mid a$ and $c\mid b$, we have
    $0 < c \leq \gcd(a, b)$
- Let $a, b, c\in \mathbb{Z}$. Suppose $a\mid bc$ and $\gcd(a, b) = 1$. Then
  $a\mid c$.
  - **Proof**: Since $\gcd(a, b) = 1$, we may use the [[Euclidean Algorithm]] to
    write $1 = ax + by$. Then $c = acx + bcy$. Since $a\mid bc$, we may rewrite
    to $c = acx + azy = a(cx + zy)$. Therefore $a\mid c$.
