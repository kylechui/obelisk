---
id: Math 110A Lecture 22
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 23]]

- **Theorem**: Let $R$ be a [[Principal Ideal Domain|principal ideal domain]],
  with $a, b\in R$ with $b\neq 0_R$. Let $d\in R$ such that $(d) = (a, b)$. Then
  $d$ is a greatest common divisor of $a$ and $b$. Moreover, if $d'\in R$, then
  $d'$ is a greatest common divisor of $a$ and $b$ if and only if $d, d'$ are
  [[Associate|associates]].
- **Proof**: The proof here is more or less identical to the Euclidean domain
  analogue.
- Let $R$ be a [[Principal Ideal Domain|principal ideal domain]]. Then all
  [[Prime Ideal|prime ideals]] are [[Maximal Ideal|maximal ideals]].
- **Proof**: Suppose $P\subseteq R$ is a [[Prime Ideal|prime ideal]]. We can
  find $p\in R$ such that $(p) = P$. We wish to show that for any ideal
  $M\supseteq P$, we have $M = P$ or $M = R$. As we are in a
  [[Principal Ideal|principal ideal]], we know that there exists $m\in R$ such
  that $M = (m)$. Since $p\in P\subseteq M$, we know there exists $r\in R$ such
  that $mr = p\in P$. Since $P$ is prime, $m\in P$ or $r\in P$.
  - Let $m\in P$. We have $M = (m)\subseteq (p) = P$. Together with our previous
    assumption that $P\subseteq M$, we have $M = P$, as we are done.
  - Let $r\in P$. We have $r\in P$, so $r = pt$ for $t\in R$. Thus
    $p = mr = mpt$, and so $mt = 1_R$. Therefore $m$ is a [[Unit|unit]], and so
    $M = (m) = R$.
- Let $R$ be an [[Integral Domain|integral domain]] and suppose $R[x]$ is a
  [[Principal Ideal Domain|principal ideal domain]]. Then $R$ is a
  [[Field|field]].
  - Show that $(x)$ is prime, and so is maximal. Then $R[x] / (x)\cong R$, which
    is a field.
- Let $R$ be a [[Principal Ideal Domain|principal ideal domain]] and $p\in R$ be
  [[Irreducibility|irreducible]]. Then $p$ is [[Prime|prime]].
- **Proof**: We proceed by showing that $(p)$ is [[Maximal Ideal|maximal]].
  Suppose $(p)\subseteq I = (a)$ for some $a\in R$. Since
  $p\in (p)\subseteq I = (a)$, we can write $p = ar$ for some $r\in R$. Since
  $p$ is [[Irreducibility|irreducible]], we know that $a$ or $r$ is a
  [[Unit|unit]].

  - If $a$ is a [[Unit|unit]], then $(a) = R$, and we are done.
  - If $r$ is a [[Unit|unit]], then $p$ and $a$ are [[Associate|associates]].
    Thus $(a) = (p)$.

    We have shown that $(p)$ is a [[Maximal Ideal|maximal ideal]], and so $(p)$
    is a [[Prime Ideal|prime ideal]]. Therefore $p$ is [[Prime|prime]].
