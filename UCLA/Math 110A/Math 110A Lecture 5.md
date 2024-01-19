---
id: Math 110A Lecture 5
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 6]]

- Let $p\in \mathbb{Z}$, where $p > 1$. Then the following are equivalent:
  1. $p$ is prime
  2. Each nonzero $[a]\in \mathbb{Z}_p$ has an inverse
  3. Let $[a], [b]\in \mathbb{Z}_p$. If $[ab] = [0]$, then $[a] = [0]$ or
     $[b] = [0]$
- **Proof**: We proceed by proving the following implications:
  - (1 $\Rightarrow$ 2) Take $[a]\in \mathbb{Z}_p$ to be nonzero. Since
    $[a] \neq [0]$, we know that $p\nmid a$. Thus $\gcd(p, a) = 1$ (since $p$ is
    prime), so there exists $x, y\in \mathbb{Z}$ such that $px + ay = 1$.
    Furthermore, we have $[px + ay] = [1]$, so $[ay] = [1]$. Therefore for all
    nonzero $[a]\in \mathbb{Z}_p$, we have $[y]\in \mathbb{Z}_p$ as its inverse.
  - (2 $\Rightarrow$ 3) Let $[a], [b]\in \mathbb{Z}_p$ such that $[ab] = [0]$.
    Without loss of generality, assume that $[a]\neq 0$. Then by (2), $[a]$ has
    an inverse, and we can multiply to get $[b] = [a]^{-1}[ab] = [0]$, as
    desired.
  - (3 $\Rightarrow$ 1) By assumption, we have that if $p\mid ab$, then
    $p\mid a$ or $p\mid b$. This implies that $p$ is prime, as desired.
    - Alternatively, suppose towards a contradiction that $p$ is not prime, so
      there exists $a, b\in \mathbb{Z}$ such that $p = ab$ and $1 < a, b < p$.
      Since $p = ab$, we know that $p\mid ab$. Thus by assumption, $p\mid a$ or
      $p\mid b$. However, since $1 < a, b < p$, we know that $p$ divides
      neither, and we have a contradiction.
- **Theorem**: Let $n\in \mathbb{Z}$ such that $n > 1$. Then $[a]$ has a
  multiplicative inverse if and only if $\gcd(a, n) = 1$.
- **Proof**:

  - ($\Rightarrow$) Suppose $[a]$ has a multiplicative inverse $[x]$ so
    $ax\equiv 1\pmod n$. Then there exists $k\in \mathbb{Z}$ such that
    $ax - 1 = kn$. Rewriting this, we have $ax - nk = 1$, so
    $\gcd(a, n) \mid 1$. This implies that $\gcd(a, n) = 1$, as desired.
  - ($\Leftarrow$) Suppose $\gcd(a, n) = 1$. By [[Bezout Identity]], there
    exists $x, y\in \mathbb{Z}$ such that $ax + ny = 1$. Thus $[ax] = [1]$, so
    $[x]$ is the inverse of $[a]$.

- [[Chinese Remainder Theorem]]
