---
id: "Translate to Intermediate Representation"
aliases:
  - "Examples"
tags:
  - "CS132"
---

- We want to write a translator from MiniJava to Sparrow
  - We are going to make it simple, at the cost of many temporaries and lots of
    code
- We have a lot of temporaries (or symbols) $t_0,\dotsc,t_n,\dotsc$ and labels
  $\ell_0,\dotsc,\ell_n,\dotsc$ which are new at the Sparrow level
- And an integer counter with initial value 0
  - We increment the counter via "gensym"
- We turn expressions $(e, k)$ into (Sparrow code$, k'$)
  - $e$ is an expression from MiniJava
  - $k$ is the counter or the first-free index; we put the result of $e$ into
    $t_k$
  - $k'$ is the counter after translating $e$
  - The main idea is that when our expression $e$ gets broken down and
    translated, it will need more memory and temporaries, and gets stored in
    values $t_k,\dotsc,t_{k'}$

## Examples

- In all of these examples, $k$ is just an index for where to store temporaries
- The expression $5, k$ gets updated to $(t_k = 5), k + 1$
- The local variable $x, k$ gets updated to $(t_k = x), k + 1$
- $\dfrac{e_1, k + 1\to code_1, k_1\quad e_2, k_1\to code_2, k_2}{e_1 + e_2,
  k\to (code_1\quad code_2\quad t_k = t_{k + 1} + t_{k_1})k_2}$

## Code

```java
class Pair {
  String code;
  int k';
}
```

```java
Pair visit(IntConst n, int k) {
  return new Pair(
    "t" + k + "=" + n.toString() + (k + 1)
  );
}

Pair visit(Plus n, int k) {
  Pair p1 = n.f0.accept(this, k + 1);
  Pair p2 = n.f2.accept(this, p1.k');
  return new Pair(
    p1.code + " " + p2.code + " " + "t" + k + "=" + "t" + (k + 1) + "+" + "t" +
    p1.k';
  );
}
```
