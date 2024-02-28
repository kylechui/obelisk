---
id: Math 110A Lecture 19
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 20]]

- **Theorem**: Let $R$ be an [[Integral Domain|integral domain]] and $p\in R$ be
  [[Prime|prime]]. Then $p$ is [[Irreducibility|irreducible]].
- **Proof**: Suppose we have some [[Prime|prime]] $p\in R$, and let $a$ be a
  [[Divisor|divisor]] of $p$. Then there exists $q\in R$ such that $aq = p$
  (note that $a \mid p$ and $q\mid p$). Since $p\mid p = aq$, and $p$ is
  [[Prime|prime]], then either $p\mid a$ or $p\mid q$.

  Without loss of generality, suppose $p\mid a$. Then there exists $r\in R$ such
  that $a = pr$. Thus $p = aq = (pr)q$, so $rq = 1$. We have found a
  multiplicative inverse for $q$, so $q$ is a [[Unit|unit]]. Therefore $p$ is
  [[Irreducibility|irreducible]] (and $p$ and $a$ are [[Associate|associates]]).

- In an [[Integral Domain|integral domain]] $R$, [[Irreducibility|irreducibles]]
  may not be [[Prime|prime]].
  - Example: Consider $\mathbb{Z}[\sqrt{-5}]$. Then we can show that
    $2, 3, 1 + \sqrt{-5}, 1 - \sqrt{-5}\in R$ are
    [[Irreducibility|irreducible]]. Then we have
    $2\cdot 3 = (1 + \sqrt{-5})(1 - \sqrt{-5})$. But $2$ does not divide either
    $1 + \sqrt{-5}$ or $1 - \sqrt{-5}$, so is not prime.
- **Theorem**: Let $R$ be an [[Integral Domain|integral domain]] and $p\in R$.
  Then $(p)$ is a [[Prime Ideal|prime ideal]] if and only if $p$ is
  [[Prime|prime]].
- [[Field of Fractions]]
- Let $R$ be an [[Integral Domain|integral domain]], and $(a, b)\sim (a', b')$
  and $(c, d)\sim (c', d')$ in its [[Field of Fractions|field of fractions]].
  Then $(ad, bc)\sim (a'd', b'c')$ and $(ad + bc, bd)\sim (a'd' + b'c', b'd')$.
