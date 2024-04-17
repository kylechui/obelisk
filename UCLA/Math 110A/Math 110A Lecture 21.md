---
id: Math 110A Lecture 21
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 22]]

- Any [[Field|field]] is a [[Euclidean domain|Euclidean domain]].
  - We can define our norm by $N(a) = 0$.
  - Thus we trivially have the first property, and the second property is
    satisfied because any element in a field is divisible by any other non-zero
    element
- **Theorem**: Let $R$ be a [[Euclidean domain]] and $I\subseteq R$ an
  [[Ideal|ideal]]. Then $I$ is a [[Principal ideal|principal ideal]]. This is
  just another way to say that all [[Euclidean domain|Euclidean domains]] are
  [[Principal Ideal Domain|principal ideal domains]].
- **Proof**: First, we consider $I = 0R$. Clearly, $I$ is principal.

  Now, consider $I\neq 0$. We claim that there exists $d\in R$ such that
  $I = dR$. Take $d\in I$. We wish to show that for all $a\in I$, we have
  $d\mid a$. Take $a\in I$. Then we can find $q, r\in R$ such that $a = dq + r$.
  Thus $r = a - dq$, so $r\in I$. However, $d$ was chosen to be of the smallest
  norm, so $r = 0$, and therefore $d\mid a$.

- **Theorem**: Let $R$ be a [[Euclidean domain|Euclidean domain]]. Let
  $a, b\in R$ such that at least one of them is nonzero. Let $d\in R$ such that
  $(d) = (a, b)$. Then $d$ is a greatest common divisor of $a$ and $b$.
- **Proof**: We wish to show that $d\mid a$ and $d\mid b$, and if there exists
  $c\in R$ such that $c\mid a$ and $c\mid b$, then $c\mid d$.

  We know that $a, b\in (a, b)$, which is a [[Principal ideal|principal ideal]],
  so $a, b\in (d)$. Thus $d\mid a$ and $d\mid b$.

  Since $d\in (d) = (a, b)$, there exists $q_1, q_2\in R$ such that
  $d = aq_1 + bq_2$. Since $c\mid a$ and $c\mid b$, we have $c\mid d$, as
  desired.
