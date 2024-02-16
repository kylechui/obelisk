---
id: Correspondence Theorem
aliases: []
tags:
  - Math110A
---

- Main idea: How can we relate [[Ideal|ideals]] in $R$ containing $I$ with
  [[Ideal|ideals]] in $R / I$ for $I\subseteq R$ an [[Ideal|ideal]].
- Let $R$ be a ring, $I$ an [[Ideal|ideal]] and consider $\pi\colon R\to R / I$.
  We abbreviate $R / I\coloneqq \overline R$. Let $J$ be an ideal in $R$, and
  $\overline J$ an ideal in $\overline R$. Then we have the following:
  1. There is a bijective correspondence between ideals in $R$ containing $I$
     and ideals of $\overline R$. In particular, given by $J\mapsto \pi(J)$ and
     $\overline J\mapsto \pi^{-1}(\overline J)$, where $\pi$ is the projection
     map from $R$ to $\overline R$.
  2. If $J$ (containing $I$) corresponds to $\overline J$ (i.e.
     $\pi(J) = \overline J$), then $R / J\cong \overline R / \overline J$.
- **Proof**:
  1. We prove that for all ideals $J\subseteq R$ and
     $\overline J\subseteq \overline R$, that $\pi(J), \pi^{-1}(\overline J)$
     are ideals.
  2. We denote the canonical projection from $\overline R$ to
     $\overline R / \overline J$ by $\phi$. Note that since $\phi$ and $\pi$ are
     surjective, so must $\phi\circ\pi$. Hence
     $\mathrm{Im}(\phi\circ\pi) = \overline R / \overline J$. Thus by the
     [[First Isomorphism Theorem]], we have that
     $R / \ker(\phi\circ\pi) \cong \overline R / \overline J$. We can show that
     $\ker(\phi\circ\pi) = J$, and we are done.
