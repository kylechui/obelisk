---
id: "Generic Type Checking"
aliases:
  - "Type Rules"
tags:
  - "CS132"
---

- Consider the following generic Java code:

```java
public class List<A> extends Object { // Classes in Java default extend Object
  public <R> R accept(ListVis<R, A> f) {
    return this.<R>accept(f);
  }
}
public class ListNull<A> extends List<A> {
  public <R> R accept(ListVis<R, A> f) {
    return f.<R>visitListNull(this);
  }
}
public class ListVis<R, A> {
  public <R> R visitListNull(List<A> arg) {
    return this.<R>visitListNull(arg);
  }
}
```

- Let us have the following type variables: $A, B, R, S, X, Y, Z$
- Also define the following grammar for generic Java:
  - $C$ is a class name
  - $X$ is a concrete type
  - $\overline T$ is a list of types

$$
\begin{align*}
  N &\Coloneqq C\langle \overline T\rangle \\
  T, V &\Coloneqq X\mid N
\end{align*}
$$

- A few examples of strings matched by the grammar:
  - `List<A>`
  - `List<ListVis<R, A>>`

## Type Rules

- $\Gamma$ is the type environment, a list of declarations of fields, variables,
  etc. with their corresponding types
- $\Gamma\vdash x : t$ says that $x$ is found in the type environment $\Gamma$,
  with type $t$
- $[\overline V / \overline Y]$ substitutes $\overline V$ for $\overline Y$
  everywhere $\overline Y$ is used

$$
\begin{gather*}
  \Gamma \vdash x : \Gamma (x) \\
  \frac{\Gamma \vdash e_0 : T_0\quad \mathrm{fields}(T_0) = \overline T
  \overline f}{\Gamma \vdash e_0 : f_i : T_i} \\
  \frac{\mathrm{fields}(N) = \overline T\overline f\quad \Gamma\vdash \overline
  e : \overline S\quad \overline S <: \overline T}{\Gamma\vdash \mathrm{new\ } N(\overline e) : N} \\
  \frac{\Gamma\vdash e_0 : T_0\quad \mathrm{mtype}(m, T_0) = \langle \overline Y\rangle\ \overline U\to U\quad \Gamma\vdash \overline e:\overline S\quad \overline S <: [\overline V / \overline Y]}{\Gamma\vdash e_0.\langle \overline V\rangle m(\overline e) : [\overline V / \overline Y]\ U} \\
  \frac{\overline x:\overline U, \mathrm{this}: C\langle\overline x\rangle\vdash e:S\quad S <: U\quad C\langle\overline x\rangle \mathrm{\ extends\ } N\quad \mathrm{override}(m, N, \langle\overline Y\rangle\ \overline U\to U)}{\langle \overline Y\rangle\ U\ m(\overline U\ \overline x) \{\ \mathrm{return\ }e;\}\quad \mathrm{OK\ in\ }C\langle\overline X\rangle}
\end{gather*}
$$
