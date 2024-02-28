---
id: Math 110A Lecture 18
aliases: []
tags:
  - Math110A
---

Next: [[Math 110A Lecture 19]]

- Let $f\in F[x]$ and $a\in F$. The remainder of $f$ divided by $x - a$ is
  $f(a)$.
- We can express $f = q(x - a) + r$, where $\deg(r) < \deg(x - a) = 1$. Thus
  $r\in F$. By plugging in $a$, we get $f(a) = q(0) + r$, so $f(a) = r$, as
  desired.
- **Theorem**: Let $f\in F[x], a\in F$. We have that $a$ is a [[Root|root]] if
  and only if $(x - a)\mid f$.
- **Proof**: By the previous lemma, we can write $f = q\cdot (x - a) + f(a)$.
  - $(\Rightarrow)$ If $a$ is a root, we have $f(a) = 0$, so $f = q(x - a)$ for
    some $q$. Therefore $(x - a)\mid f$.
  - $(\Leftarrow)$ Suppose $(x - a)\mid f$. Then $f = q(x - a)$ for some $q$, so
    $f(a) = 0$.
- **Theorem**: Suppose $f\in F[x]$ with $\deg(f) = n\geq 1$. Then $f$ has at
  most $n$ roots.
