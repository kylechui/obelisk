---
id: First Isomorphism Theorem
aliases: []
tags:
  - Math110A
---

- **Theorem**: Let $f\colon R\to S$ be a
  [[Ring Homomorphism|ring homomorphism]]. The following hold:

  1. There exists a unique homomorphism $\bar f\colon R / \ker(f)\to S$ such
     that $f = \bar f\circ \pi$
  2. $R / \ker(f)\cong \mathrm{Im}(f)$

  In other words, there exists a unique arrow $\bar f$ such that this diagram
  commutes: ![](./first_isomorphism_theorem_cd.png)

**Proof**: We define $\bar f$ by $a + \ker(f)\mapsto f(a)$.

- We first show that this mapping is a well-defined function. Suppose
  $a + \ker(f) = a' + \ker(f)$. Then we know that $a - a'\in \ker(f)$, so
  $f(a - a') = 0$. Since $f$ is a [[Ring Homomorphism|ring homomorphism]], we
  know that $f(a) - f(a') = 0$, so $f(a) = f(a')$.
- Next, we show that $\bar f$ is a [[Ring Homomorphism|ring homomorphism]].
  - Observe that $\bar f(1_R + \ker(f)) = f(1_R) = 1_S$.
  - Observe that
    $$
    \begin{align*}
      \bar f((a + \ker(f)) + (b + \ker(f))) &= f(a + b) \\
      &= f(a) + f(b) \\
      &= \bar f(a + \ker(f)) + \bar f(b + \ker(f)).
    \end{align*}
    $$
  - Observe that
    $$
    \begin{align*}
      \bar f((a + \ker(f))(b + \ker(f))) &= \bar f(ab + \ker(f)) \\
      &= f(ab) \\
      &= f(a)f(b) \\
      &= \bar f(a + \ker(f))\bar f(b + \ker(f)).
    \end{align*}
    $$
- It remains to be shown that $f = \bar f\circ \pi$ and that $\bar f$ is unique.
  - $(\bar f\circ \pi)(a) = \bar f(a + \ker (f)) = f(a)$
  - Suppose towards a contradiction that there exists $g\colon R/\ker (f)\to S$
    with $g\not\equiv \bar f$. So there exists $b + \ker(f)$ such that
    $g(b + \ker(f))\neq \bar f(b + \ker(f))$. Then
    $$
    \begin{align*}
      (g\circ \pi)(b) &= g(b + \ker(f)) \\
      &\neq \bar f(b + \ker(f)) \\
      &= f(b).
    \end{align*}
    $$
    Thus we have a contradiction since the diagram no longer commutes, so
    $\bar f$ must be unique.
- Now we show that $R / \ker(f)\cong \mathrm{Im}(f)$.
  - We know that $\mathrm{Im}(\bar f)\subseteq \mathrm{Im}(f)$, since every
    input to $\bar f$ just gets mapped to some output in the image of $f$.
  - We now show that $\bar f$ is injective. All elements in the kernel should
    satisfy $\bar f(a + \ker(f)) = f(a) = 0_S$, so $a\in \ker(f)$. Hence
    $a + \ker(f) = 0_R + \ker(f)$, and $a + \ker(f) = 0_{R / \ker(f)}$. Thus we
    see that $\bar f$ maps $0_{R / \ker(f)}$ to $0_S$. This tells us that when
    we restrict the codomain to $\mathrm{Im}(f)$ (also equal to
    $\mathrm{Im}(\bar f)$), we have $\bar f\colon R / \ker(f)\to \mathrm{Im}(f)$
    an isomorphism.
