---
id: Fundamental Theorem of Arithmetic
aliases: []
tags:
  - Math110A
---

- Let $n\in\mathbb{Z}$ such that $n\neq 0, \pm 1$. Suppose we can write
  $n = p_1 \dotsb p_r$ and $n = q_1 \dotsb q_s$, where $p_i, q_j$ are prime for
  all $i, j$. Then $r = s$ and there is a permutation $\sigma$ on
  $\left\{1,\dotsc,r\right\}$ such that $p_i = \pm q_{\sigma(i)}$
  - **Proof**: Let $n = p_1 \dotsb p_r = q_1 \dotsb q_s$. Thus there exists some
    $j$ such that $p_1\mid q_j$. Since both are prime, $p_1 = \pm q_j$. Without
    loss of generality, we may assume $j = 1$, so $q_1 = \pm p_1$. Therefore
    $p_1 p_2\dotsb p_r = \pm p_1 q_2 \dotsb q_s$. Dividing both sides by $p_1$,
    it suffices to show $p_2 \dotsb p_r = \pm q_2 \dotsb q_s$. Without loss of
    generality, suppose $r \leq s$. Repeating this process yields
    $1 = \pm q_{r + 1} \dotsb q_s$. This implies that all of
    $\left\{q_r + 1,\dotsc,q_s\right\}$ are $\pm 1$, contradicting that they are
    prime. Therefore $r = s$, and we are done.
