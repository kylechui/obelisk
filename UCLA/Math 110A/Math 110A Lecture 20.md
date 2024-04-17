---
id: Math 110A Lecture 20
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 21]]

- Multiplication is well-formed in the
  [[Field of Fractions|field of fractions]].
- **Proof**: Let $(a, b)\sim (a', b')$ and $(c, d)\sim (c', d')$. We claim that
  $(ac, bd)\sim (a'c', b'd')$. Thus we need to show $acb'd' = a'c'bd$. Since
  $(a, b)\sim (a', b')$, we know that $ab' = a'b$. Similarly, as
  $(c, d)\sim (c', d')$, we know that $cd' = c'd$. Therefore we have
  $$
  \begin{align*}
    acb'd' &= (ab')(cd') \\
           &= (a'b)(c'd) \\
           &= a'c'bd,
  \end{align*}
  $$
  as desired.
- Using this and the fact that addition is well-defined, we can define:
  - $[(a, b)] + [(c, d)] = [(ad + bc, bd)]$
  - $[(a, b)] \cdot [(c, d)] = [(ac, bd)]$
- **Notation**: Given $[(a, b)]\in S(R) / \sim$, we refer to this equivalence
  class as $\frac{a}{b}$.
- To view $R\subseteq \mathrm{Frac}(R)$, consider
  $f\colon R\to \mathrm{Frac}(R)$ by $r\mapsto \frac{r}{1}$. We claim that $f$
  is a [[Ring Homomorphism|ring homomorphism]] and injective.
  - To show injectivity, consider $f(r) = 0$. Then we have $\frac{r}{1} = 0$, so
    $r = 0$, as desired.
- Let $F$ be a [[Field|field]]. Then $F\cong \mathrm{Frac}(F)$.
- We need that $R$ be an [[Integral Domain|integral domain]] to ensure that we
  don't accidentally "divide by zero" anywhere, e.g.
  $(1, a)\cdot (1, b) = (1, ab)$ for $a, b$ nonzero.
