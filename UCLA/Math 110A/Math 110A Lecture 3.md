---
id: Math 110A Lecture 3
aliases: []
tags:
  - Math110A
---

- **Theorem**: Let $p\in \mathbb{Z}$ such that $p\neq 0, \pm 1$. The following
  are equivalent:

  1. $p$ is prime
  2. If $p\mid bc$ where $b, c\in \mathbb{Z}$, then $p\mid b$ or $p\mid c$

  - **Proof**:

    - ($1 \Rightarrow 2$) Suppose $p$ is prime and $p\mid bc$. Since $p$ is
      prime, we know that $\gcd(p, b) = 1$ or $\gcd(p, b) = p$. Without loss of
      generality, suppose $p\nmid b$. If $\gcd(p, b) = p$, then that implies
      $p\mid b$, a contradiction. Hence $\gcd(p, b) = 1$. By
      [[Bezout Identity]], there exists $k_1, k_2\in \mathbb{Z}$ such that:

      $$
      \begin{align*}
        k_1p + k_2b &= 1 \\
        k_1pc + k_2bc &= c \\
        k_1pc + k_2(kp) &= c \tag{$p\mid bc$} \\
        p(k_1c + k_2k) &= c.
      \end{align*}
      $$

      Therefore $p\mid c$.

    - ($2 \Rightarrow 1$) Suppose towards a contradiction that $p$ is not prime,
      so $p = mn$, where $m, n\neq 0, \pm 1$. Let $b = m, c = n$. Then
      $p\mid bc$, but $p\nmid b$ and $p\nmid c$ (since $p < b, c$), a
      contradiction. Therefore $p$ must be prime.

- **Corollary**: If $p$ is prime and $p\mid a_1 \dotsb a_n$, there must be at
  least one $a_i$ such that $p\mid a_i$
- **Theorem**: Let $n\in \mathbb{Z}$ be nonzero and $n\neq \pm 1$. Then $n$ can
  be written as a product of primes

  - **Proof**: For $n < 1$, we note $n = -(-n)$, where $-n > 1$. In this case,
    we can apply the following argument. Consider $n > 1$, and let $S$ be the
    set of positive numbers greater than 1 that cannot be written as a product
    of primes.

    Suppose towards a contradiction that $S\neq \varnothing$, and since
    $S\subseteq \mathbb{Z}_{\geq 0}$, it contains a minimal element by the
    [[Well-Ordering Principle]]; call it $m$. In particular, $m$ is not a
    product of primes and $m$ is not prime. Since $m$ is not prime, there exists
    some $a\in \mathbb{Z}$ such that $a\neq \pm 1, \pm m$ and $a\mid m$. We
    write $m = a\cdot b$. Without loss of generality, suppose $a > 0$, $b > 0$.
    Furthermore, we have $|a| \leq |m| = m$, and $|b|\leq |m| = m$. Also note
    that $b\neq 1$, otherwise $a = m$.

    Thus we have $1 < a, b < m$, and so $a, b\notin S$ (since $m$ is the minimal
    element of $S$). Since $a, b$ can be written as the product of primes, so
    can $m$. However $m\in S$, a contradiction, so $S = \varnothing$ and $n$ can
    be written as a product of primes.

- [[Fundamental Theorem of Arithmetic]]
