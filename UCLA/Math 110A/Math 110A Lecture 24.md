---
id: Math 110A Lecture 24
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 25]]

- Any [[Principal Ideal Domain|PID]] is a [[Unique Factorization Domain|UFD]]
- Given a [[Unique Factorization Domain|UFD]] $R$, we have $R[x]$ is also a
  [[Unique Factorization Domain|UFD]]
- $\mathbb{Z}[x]$ is an example of a [[Unique Factorization Domain|UFD]] that is
  not a [[Principal Ideal Domain|PID]]
- Let $R = F[x_1,\dotsc,x_n]$ be the polynomials with $F$-coefficients. If
  $n > 1$, $R$ is _not_ a [[Principal Ideal Domain|PID]], but _is_ a
  [[Unique Factorization Domain|UFD]]
- **Theorem**: Let $R$ be a [[Unique Factorization Domain|UFD]], with $r\in R$.
  Then $r$ is [[Prime|prime]] if and only if $r$ is
  [[Irreducibility|irreducible]].
- **Proof**: If $r$ is [[Prime|prime]], it is also
  [[Irreducibility|irreducible]], since $R$ is an
  [[Integral Domain|integral domain]]. Suppose $r$ is
  [[Irreducibility|irreducible]]. Suppose $r\mid ab$, so there exists some
  $c\in R$ such that $rc = ab$. Note that one of $a, b$ is not a [[Unit|unit]],
  since $r$ is [[Irreducibility|irreducible]]. Without loss of generality, we
  can write $b = q_1 \dotsb q_m$. If $a$ is a [[Unit|unit]], we may write
  $ab = (aq_1)q_2 \dotsb q_m$. If $a$ is _not_ a [[Unit|unit]], then
  $a = p_1 \dotsb p_n$, so $ab = p_1 \dotsb p_n q_1 \dotsb q_m$. Because $R$ is
  a [[Unique Factorization Domain|UFD]] and $r$ [[Irreducibility|irreducible]],
  we know that $r$ must be [[Associate|associates]] with one of the $p_i$ or
  $q_j$. This implies $r\mid a$ or $r\mid b$, and we are done.
- **Theorem**: Let $R$ be a [[Unique Factorization Domain|UFD]] with
  $a, b\in R$. We can write $a = up_1^{e_1} \dotsb p_n^{e_n}$ and
  $b = vp_1^{f_1} \dotsb p_n^{f_n}$, for $u, v\in R$ [[Unit|units]] and
  $e_i, f_j\geq 0$, such that $p_i, p_j$ are not associates for $i\neq j$. For
  each $i$, define $m_i = \min(e_i, f_i)$. Then $d = p_1^{m_1}\dotsb p_n^{m_n}$
  is the greatest common divisor of $a, b$.
- **Proof**: By construction, it is clear $d\mid a$ and $d\mid b$. Suppose
  $c = w q_1^{g_1} \dotsb q_n^{g_n}$ such that $c\mid a$ and $c\mid b$, and
  where $w$ is a [[Unit|unit]] and $q_i$ is [[Prime|prime]] for all $q$. It
  suffices to show $c\mid d$. Since $q_i\mid c$ for all $i$, we have
  $q_i\mid a, b$. As all the $p_j$ are prime, we know that $q_i$ is an associate
  for some $p_j$. Thus we can write
  $c = k p_1^{\alpha_1} \dotsb p_n^{\alpha_n}$, for some [[Unit|unit]] $k$. Note
  that $\alpha_i\leq e_i$, as otherwise $c\nmid a$. Similarly,
  $\alpha_i\leq f_i$. Therefore $\alpha_i\leq \min(e_i, f_i) = m_i$, and
  $c\mid d$.
- **Theorem**: Let $R$ be an [[Integral Domain|integral domain]]. Then $R$ is a
  [[Unique Factorization Domain|UFD]] if and only if $R$ satisfies the
  [[Ascending Chain Condition|ascending chain condition]] on
  [[Principal Ideal|principal ideals]] and [[Irreducibility|irreducibles]] are
  [[Prime|prime]].
  - Note: The [[Ascending Chain Condition|ACCP]] gives us that factorizations
    exist, and irreducibles being prime gives us uniqueness.
