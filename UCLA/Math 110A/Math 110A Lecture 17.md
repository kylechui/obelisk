---
id: Math 110A Lecture 17
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 18]]

- Let $f, g\in F[x]$. We say that $f$ _divides_ $g$ ($f\mid g$) if there exists
  some polynomial $s\in F[x]$ such that $g = f\cdot s$. We say that $f$ is a
  _divisor_ of $g$.
- Let $f, g\in F[x]$, where $g\neq 0$, and $f\mid g$. Then $\deg(f)\leq\deg(g)$.
- **Proof**: We can find some $s\in F[x]$ such that $f\cdot s = g$. Then we have
  that $\deg(g) = \deg(f\cdot s) = \deg(f) + \deg(s)$. Since $g\neq 0$, we also
  have $s\neq 0$. Therefore $\deg(s)\geq 0$, so $\deg(f)\leq\deg(g)$.
- Let $f, g\in F[x]$, with at least one of the two nonzero. Then the greatest
  common divisor of $f$ and $g$ is the unique monic polynomial $d\in F[x]$ with
  the largest degree that divides both $f$ and $g$.
  - $d\mid f$ and $d\mid g$.
  - If $a\mid f$ and $a\mid g$ then $a\mid d$.
- Let $f, g\in F[x]$ not both zero. We can find $m, n\in F[x]$ such that
  $fm + gn = \gcd(f, g)$.
- Let $a, b, c\in F[x]$. Suppose that $a\mid bc$ and $\gcd(a, b) = 1$. Then
  $a\mid c$.
- **Proof**: Since $\gcd(a, b) = 1$, we can find $m, n\in F[x]$ such that
  $am + bn = 1$. Then $acm + bcn = c$. Since $a\mid bc$, there exists some
  $k\in F[x]$ such that $ak = bc$. Thus we have $acm + akn = a(cm + kn) = c$.
  Therefore $a\mid c$.
- **Theorem**: Let $p\in F[x]$. Then the following are equivalent:
  1. $p$ is [[Irreducibility|irreducible]].
  2. If $p\mid ab$ then $p\mid a$ or $p\mid b$.
  3. If $p = ab$ then $a$ is a [[Unit|unit]] or $b$ is a [[Unit|unit]].
- (1 $\Rightarrow$ 2): Suppose that $p$ is [[Irreducibility|irreducible]] and
  $p\mid ab$. Without loss of generality, suppose $p\nmid a$. Then we have
  $\gcd(a, p) = 1$, so $p\mid b$, as desired.

  (2 $\Rightarrow$ 3): Suppose that $p = ab$. Note that
  $\deg(a), \deg(b)\leq \deg(ab) = \deg(p)$. Since $p\mid ab$, then $p\mid a$ or
  $p\mid b$. Without loss of generality, suppose $p\mid a$. Then
  $\deg(p)\leq \deg(a)$. Therefore $\deg(p) = \deg(a)$, so $\deg(b) = 0$, and
  $b$ is a [[Unit|unit]], as desired.

  (3 $\Rightarrow$ 1): Suppose $p = ab$. Then we know that $a$ is a
  [[Unit|unit]] or $b$ is a [[Unit|unit]]. Without loss of generality, let $a$
  be a [[Unit|unit]]. Then we know that $\deg(a) = 0$, so
  $\deg(b) = \deg(p) - \deg(a) = \deg(p)$. Therefore $b$ is an
  [[Associate Polynomial|associate]] for $p$, as desired.

- If $p\in F[x]$ is [[Irreducibility|irreducible]] and $p\mid a_1a_2\cdots a_n$,
  then $p\mid a_i$ for some $i$.
- **Theorem**: Let $f\in F[x]$ be a nonzero and non-constant, i.e. $f$ is not a
  [[Unit|unit]]. Then $f$ can be factored into a product of
  [[Irreducibility|irreducible polynomials]]. Moreover, this factorization is
  unique, i.e. if $f = p_1 \dotsb p_n = q_1 \dotsb q_m$, where $p_i$ and $q_j$
  are [[Irreducibility|irreducible]], then $n = m$ and there exists a
  permutation $\sigma$ on $\{1,\dotsc,n\}$ such that $p_i$ and $q_{\sigma(i)}$
  are [[Associate Polynomial|associates]].
- **Proof**: Let $S$ be the set of functions in $F[x]$ such that $f$ is not a
  [[Unit|unit]], is nonzero, and cannot be written as the product of
  [[Irreducibility|irreducibles]]. We seek to show that $S$ is nonempty. Suppose
  towards a contradiction that $S$ is empty. Then we choose $f\in S$ to be of
  lowest degree. Since $f$ is not a [[Unit|unit]] (and nonzero), then
  $\deg(f)\geq 1$. Note that $f$ cannot be irreducible, since we allow products
  of just one element and it is in $S$.

  Thus we may write $f = ab$ for some nonzero and non-[[Unit|unit]]
  $a, b\in F[x]$. Since $\deg(f) = \deg(a) + \deg(b)$, we have
  $\deg(a), \deg(b) < \deg(f)$. Thus as $f$ has minimal degree in $S$, we know
  that $a, b\notin S$. Therefore $a$ and $b$ can be written as the product of
  [[Irreducibility|irreducibles]]. Thus $f$ can be written as the product of
  [[Irreducibility|irreducibles]], a contradiction. Therefore $S$ is nonempty.

  Suppose $p_1 \dotsb p_n = q_1 \dotsb q_m$, where $p_i, q_j$ are
  [[Irreducibility|irreducible]]. Note that $p_1\mid q_1 \dotsb q_m$. Thus
  without loss of generality, we may assume that $p_1\mid q_1$. Since $p_1, q_1$
  are [[Irreducibility|irreducible]], then $p_1 = c_1q_1$ for some $c_1\in F$.
  Without loss of generality, let $n \leq m$. Then we repeat this process $n$
  times, yielding $c_1 \dotsb c_n q_1 \dotsb q_n = q_1 \dotsb q_m$. Cancelling
  on both sides gives $c_1 \dotsb c_n = q_{n + 1} \dotsb q_m$. Since the left
  hand side is a unit, we can find some multiplicative inverse $k\in F$. Then
  $k(q_{n + 1} \dotsb q_{m - 1})$ is a multiplicative inverse for $q_m$, so
  $q_m$ is a [[Unit|unit]]. However this contradicts that $q_m$ is
  [[Irreducibility|irreducible]], so we are done.
