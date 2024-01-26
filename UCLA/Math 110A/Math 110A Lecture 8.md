---
id: Math 110A Lecture 8
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 9]]

- A [[Ring Homomorphism|ring homomorphism]] that does not map units to units is
  said to be _non-unital_
- A map $f\colon R\to S$ such that $f(r) = 0_S$ for all $r\in R$ is not a
  [[Ring Homomorphism|ring homomorphism]] unless $S = \{0_S\}$.
- Let $R$ and $S$ be [[Ring|rings]] and $f\colon R\to S$ be a
  [[Ring Homomorphism|ring homomorphism]]. Given $a, b\in R$, the following
  hold:
  1. $f(0_R) = 0_S$
  2. $f(-a) = -f(a)$
  3. $f(a-b) = f(a) - f(b)$
  4. If $a\in R$ is a [[Unit|unit]], then $f(a)$ is a unit, with
     $f(a)^{-1} = f(a^{-1})$
- **Proof**:
  1. $f(0_R) = f(0_R + 0_R) = f(0_R) + f(0_R)\implies f(0_R) = 0_S$
  2. $f(a) + f(-a) = f(a + (-a)) = f(0_R) = 0_S\implies -f(a) = f(-a)$
  3. $f(a-b) = f(a + (-b)) = f(a) + f(-b) = f(a) - f(b)$
  4. $f(a)f(a^{-1}) = f(aa^{-1}) = f(1_R) = 1_S\implies f(a)$ is a unit with
     inverse $f(a^{-1})$
- [[Ring Isomorphism]]
- Let $f\colon R\to S$ be a [[Ring Homomorphism|ring homomorphism]]. The
  _kernel_ of $f$ is defined by $\ker(f) = \{a\in R\mid f(a) = 0_S\}$ and the
  image of $f$ is $\mathrm{im}(f) = \{f(a)\mid a\in R\}$
- Let $f\colon R\to S$ be a [[Ring Homomorphism|ring homomorphism]]. Then
  $\mathrm{im}(f)$ is a [[Subring|subring]] of $S$ and $\ker(f)$ is a
  [[Non-unital Rings|non-unital subring]] of $R$.
- **Proof**: To show that $\mathrm{im}(f)$ is a [[Subring|subring]] of $S$, we
  need to show:

  1. Closure of addition
  2. Closure of multiplication
  3. Closure of additive inverses
  4. $1_S\in \mathrm{im}(f)$

  We show for $f(a), f(b)\in \mathrm{im}(f)$:

  1. $f(a) + f(b) = f(a + b) \in \mathrm{im}(f)$
  2. $f(a)f(b) = f(ab) \in \mathrm{im}(f)$
  3. $-f(a) = f(-a) \in \mathrm{im}(f)$
  4. $f(1_R) = 1_S \in \mathrm{im}(f)$

  To show that $\ker(f)$ is a [[Non-unital Rings|non-unital subring]] of $R$, we
  need to show:

  1. Closure of addition
  2. Closure of multiplication
  3. Closure of additive inverses
  4. $0_R\in \ker(f)$

  We show for $a, b\in \ker(f)$:

  1. $0_S = 0_S + 0_S = f(a) + f(b) = f(a + b)$, so $a + b\in \ker(f)$
  2. $0_S = 0_S0_S = f(a)f(b) = f(ab)$, so $ab\in \ker(f)$
  3. $0_S = -f(a) = f(-a)$, so $-a\in \ker(f)$
  4. $0_S = f(0_R)$, so $0_R\in \ker(f)$

- Let $f\colon R\to S$ be a [[Ring Homomorphism|ring homomorphism]]. Then for
  any $a\in \ker(f)$ and $b\in R$, we have $ab, ba\in \ker(f)$.
- **Proof**: $f(ab) = f(a)f(b) = 0_Sf(b) = 0_S$. Similarly, $f(ba) = 0_S$.
- Let $R$ be any ring. Then there is a unique
  [[Ring Homomorphism| homomorphism]] $f\colon \mathbb{Z}\to R$.
  - This is because any $n\in \mathbb{Z}$ can be written as a sum of $1_R$s, so
    any $f(n)$ is defined by $f(1) = 1_R$.
