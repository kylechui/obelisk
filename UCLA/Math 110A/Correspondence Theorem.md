---
id: Correspondence Theorem
aliases: []
tags:
  - Math110A
---

- Main idea: How can we relate [[Ideal|ideals]] in $R$ with [[Ideal|ideals]] in
  $R / I$ for $I\subseteq R$ an [[Ideal|ideal]].
- Let $R$ be a ring, $I$ an [[Ideal|ideal]] and consider $\pi\colon R\to R / I$.
  We abbreviate $R / I\coloneqq \bar R$. Let $J$ be an ideal in $R$, and
  $\bar J$ an ideal in $\bar R$. Then we have the following:
  1. There is a bijective correspondence between ideals in $R$ containing $I$
     and ideals of $\bar R$. In particular, given by $J\mapsto \pi(J)$ and
     $\bar J\mapsto \pi^{-1}(\bar J)$, where $\pi$ is the projection map from
     $R$ to $\bar R$.
  2. If $J$ corresponds to $\bar J$ (i.e. $\pi(J) = \bar J$), then
     $R / J\cong \bar R / \bar J$.
