---
id: Well-Ordering Principle
aliases: []
tags:
  - Math110A
---

- Every non-empty set of non-negative integers contains a smallest element
  - We can find $a\in S$ such that $\forall b\in S, a \leq b$
- **Proof**: Let $S$ be a set of non-negative integers. Suppose there is no
  smallest element. Thus $0\notin S$, since 0 is less than or equal to all
  non-negative integers. By induction, suppose $0,\dotsc,n\notin S$. Then
  $n + 1\notin S$ as well, otherwise $n + 1$ would be the smallest element.
  Therefore the set must be empty.
