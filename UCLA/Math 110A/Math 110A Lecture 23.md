---
id: Math 110A Lecture 23
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 24]]

- If an [[Ideal|ideal]] $I$ is not finitely generated, we can find
  $a_1,a_2,\dotsc \in I$ such that
  $$
    (a_1)\subsetneq (a_2) \subsetneq \dotsb
  $$
- **Theorem**: A [[Principal Ideal Domain|principal ideal domain]] $R$ satisfies
  the [[Ascending Chain Condition|ascending chain condition]]
- **Proof**: Let $(a_1)\subseteq (a_2)\subseteq \dotsb$ be an
  [[Ascending Chain Condition|ascending chain]] of
  [[Principal Ideal|principal ideals]]. Consider
  $I = \cup_{i = 1}^\infty (a_i)$, which is an [[Ideal|ideal]]. Since
  $I\subseteq R$, $I$ is [[Principal Ideal|principal]]. Thus we can find
  $a\in I$ such that $I = (a)$. Because $a\in I = \cup_{i = 1}^\infty (a_i)$, we
  can find $n$ such that $a\in (a_n)$.

  We claim that $(a_n) = I$. We have that $(a_n)\subseteq I$ because
  $I = \cup_{i = 1}^\infty (a_i)$. Since $I = (a)$ and $a\in (a_n)$, we have
  $I\subseteq (a_n)$. Thus $I = (a_n)$.

  Thus for all $m\geq n$, we have $(a_m) = (a_n)$.

- **Theorem**: Let $R$ be an [[Integral Domain|integral domain]] that satisfies
  the [[Ascending Chain Condition|ascending chain condition]]. Then every
  nonzero and nontrivial element of $R$ can be written as a product of
  [[Irreducibility|irreducibles]].
- **Proof**: Let $r\in R$ be nonzero and not a [[Unit|unit]]. Suppose towards a
  contradiction that $r$ cannot be written as a product of
  [[Irreducibility|irreducibles]]. Then $r$ is not
  [[Irreducibility|irreducible]], so we can write $r = r_1^1r_2^1$, where
  $r_1^1,r_2^1$ are not [[Unit|units]]. At least one of $r_1^1, r_2^1$ is not a
  product of [[Irreducibility|irreducibles]], otherwise $r$ would be as well.
  Without loss of generality, we assume $r_1^1$ is not a product of
  [[Irreducibility|irreducibles]]. Thus we may write $r_1^1 = r_1^2r_2^2$, where
  neither is a [[Unit|unit]]. Repeating this argument, we get a sequence of
  $r_1^i$, where $(r_1^1)\subseteq (r_1^2)\subseteq \dotsb$. Moreover we
  actually have $(r_i^i)\subsetneq (r_1^{i + 1})$, since
  $r_1^i = r_1^{i + 1}r_2^{i + 1}$ and $r_2^{i + 1}$ is not a [[Unit|unit]].
  This contradicts the [[Ascending Chain Condition]], so we are done.
