---
id: Math 180 Lecture 3
aliases: []
tags:
  - Math180
---

Next: [[Math 180 Lecture 4]]

- **Theorem**: The number of [[Composition|compositions]] of $n$ with $k$ parts
  is $\binom{n - 1}{k - 1}$
  - This is because out of $n - 1$ "dividers" between elements, we are choosing
    $k - 1$ to split our set into $k$ parts
- **Theorem**: The number of [[Weak Composition|weak compositions]] of $n$ with
  $k$ parts is $\binom{n + k - 1}{k - 1}$
  - This is because our $k - 1$ dividers are added to our original list of $n$
    elements, giving us $n + k - 1$ total objects
  - Another approach is to define $b_i\coloneqq a_i + 1$, and count the number
    of [[Composition|compositions]] adding up to $\sum b_i = n + k$

## Binomial Identities

- $\binom{n}{k} = \binom{n}{n - k}$
  - Choosing $k$ objects from $n$ to form a subset is the same as choosing
    $n - k$ objects and _excluding_ them
- $\binom{n}{0} + \binom{n}{1} + \dotsb + \binom{n}{k} = 2^n$
  - The left-hand side counts the total number of subsets of a set with
    cardinality $n$, since $\binom{n}{i}$ is the number of subsets with
    cardinality $i$. The right-hand side counts the same, by using the
    [[Counting Principles|multiplication principle]] and including/excluding
    each element (2 choices for $n$ elements)
- $\binom{n}{0} + \binom{n}{2} + \binom{n}{4} + \dotsb = \binom{n}{1} + \binom{n}{3} + \binom{n}{5} + \dotsb$
  - The left-hand side counts the total number of subsets with even cardinality,
    while the right-hand side counts the total number of subsets with odd
    cardinality. Consider $1\in [n]$. We consider a function
    $f\colon [n]\to [n]$ defined by:
    $$
    f(S) = \begin{cases}
      S\cup \{1\} &\text{if } 1\notin S \\
      S\setminus \{1\} &\text{if } 1\in S
    \end{cases}
    $$
    Note that since we are always adding or removing one element from $S$, that
    $S$ and $f(S)$'s cardinalities always have opposite parity
- $\sum_{k = 0}^n k\binom{n}{k} = n2^{n - 1}$
  - Both sides count the number of committees that exist with one chairperson.
    The left-hand side constructs the committee by ranging over $k$, first
    choosing $k$ people to form the committee then out of the $k$ people
    choosing the chairperson. The right-hand side first chooses the chairperson
    ($n$ choices), then chooses a subset of the remaining $n - 1$ people to be
    on the committee
- The [[Binomial Theorem]] is a generating function for the binomial
  coefficients
- $\sum_k \binom{n}{k}\binom{m}{\ell - k} = \binom{n + m}{\ell}$
  - The right-hand side counts the number of subsets of cardinality $\ell$ from
    a set of cardinality $n + m$. Another way to do this is to first split our
    set into two sets of size $n$ and $m$, respectively. Then from the first,
    choose $k$ elements, and from the latter choose the remaining $\ell - k$
    elements. Taking the union of these subsets gives us a subset of size $\ell$
    from all $n + m$ elements. Summing this expression for all $k$ gives us all
    possible the number of subsets of size $\ell$ from a total of $n + m$
    elements.
