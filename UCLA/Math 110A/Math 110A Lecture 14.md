---
id: Math 110A Lecture 14
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 15]]

## (Non)Examples of [[Prime Ideal|Prime Ideals]]

- $R = \mathbb{Z} / 6\mathbb{Z}$, consider $I = 0\subseteq R$.
  - This is _not_ a [[Prime Ideal|prime ideal]], because while $[2][3] = [0]$,
    we have $[2]\neq [0]$ and $[3]\neq[0]$.
- Let $R = \mathbb{Z}$, and let $n\neq 0, \pm 1$ be composite. Then
  $n\mathbb{Z}$ is _not_ a [[Prime Ideal|prime ideal]] because we can always
  find $a, b\neq 0$ such that $ab \equiv 0\pmod n$.
- If $p$ is prime, then $p\mathbb{Z}$ is a [[Prime Ideal|prime ideal]] in
  $R = \mathbb{Z}$. This is because for some $a, b\in \mathbb{Z}$, if $ab = p$,
  then $p\mid a$ or $p\mid b$. Hence $a\in p\mathbb{Z}$ or $b\in p\mathbb{Z}$.
- Let $R$ be an [[Integral Domain|integral domain]]. Then $\{0\}\subseteq R$ is
  a [[Prime Ideal|prime ideal]].
- Let $R = \mathbb{R}[x, y]$. Then $xR$ is a [[Prime Ideal|prime ideal]], but
  not [[Maximal Ideal|maximal]].
