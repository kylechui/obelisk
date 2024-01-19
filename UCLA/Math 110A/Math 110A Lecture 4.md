---
id: Math 110A Lecture 4
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 5]]

- Let $n \in \mathbb{Z}_{>0}$. The integers [[Modulo|modulo]] $n$, which we
  abbreviate as $\mathbb{Z}_n$ or $\mathbb{Z}/n$ is the set of congruence
  classes of integers [[Modulo|modulo]] $n$
- Let $n \in \mathbb{Z}_{>0}$, and let $[a], [b]\in \mathbb{Z}_n$. We define:
  - $[a] + [b] = [a + b]$
  - $[a][b] = [ab]$
- **Theorem**: Let $n \in \mathbb{Z}$. Suppose $[a] = [a']$ and $[b] = [b']$.
  The following are true:

  - $[a+b] = [a' + b']$
  - $[ab] = [a'b']$

- **Proof**: Since $[a] = [a']$ and $[b] = [b']$, we know that $n\mid (a - a')$
  and $n\mid (b - b')$. We use the fact that
  $(a + b) - (a' + b') = (a - a') + (b - b')$. Because $(a - a')$ and $(b - b')$
  are both divisible by $n$, we have $n\mid ((a + b) - (a' + b'))$, so
  $[a + b] = [a' + b']$.

  For the second part, we have that:

  $$
  \begin{align*}
    ab - a'b' &= ab - a'b + a'b - a'b' \\
              &= b(a - a') + a'(b - b').
  \end{align*}
  $$

  By similar reasoning as before, we have that $[ab] = [a'b']$.

- Let $n > 1$ be an integer, and consider $[a] \in \mathbb{Z}_n$. If there
  exists $[b] \in \mathbb{Z}_n$ such that $[a][b] = [1]$, then we say $[a]$ is a
  _unit_, and $[b]$ is the _inverse_ of $[a]$.
