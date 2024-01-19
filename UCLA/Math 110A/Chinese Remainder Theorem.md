---
id: Chinese Remainder Theorem
aliases: []
tags:
  - Math110A
---

- Let $m, n\in \mathbb{Z}$ such that $\gcd(m, n) = 1$ and $m, n > 1$. Let
  $a, b\in \mathbb{Z}$. We can find $x$ such that $x\equiv a\pmod m$ and
  $x\equiv b\pmod n$. If $y$ is another solution, then $y\equiv x\pmod{mn}$.
- **Proof**: Since $\gcd(m, n) = 1$, there exist $c, d\in \mathbb{Z}$ such that
  $mc + nd = 1$. Thus $cm\equiv 1\pmod n$, and $dn\equiv 1\pmod m$. Therefore
  $acm\equiv a\pmod n$ and $bdn\equiv b\pmod m$. Adding these together, we
  choose $x = acm + bdn$, which satisfies the desired properties.

  If $y$ is another solution, then we know that $x\equiv y\pmod m$ and
  $x\equiv y\pmod n$. Since $\gcd(m, n) = 1$, we know that $mn\div x - y$, so
  $x\equiv y\pmod{mn}$.
