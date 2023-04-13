---
id: "Type Checking"
aliases:
  - "Implementation"
tags:
  - "CS132"
---

- The type checker takes in an input program and outputs whether or not the
  program is valid, according to the type rules
- For each operator node, recursively validate the type of its children nodes
  and then validate whether or not the operator has valid arguments
- We write `⊢ e : t` to denote that the expression `e` has type `t`
- Type checking rules are written using the following notation:
  $$
  \frac{Hypothesis_1 ... Hypothesis_n}{Conclusion}
  $$
  where the "numerator" evaluates to the "denominator"
  - We can rewrite this as $H_1\land H_2\land\dotsb\land H_n\implies C$
  - Each of the rules (and the conclusion) takes the form `⊢ e : t`
- Rules for MiniJava:
  - $\vdash false : boolean$
  - $\vdash true : boolean$
  - $\dfrac{\vdash e : boolean}{\vdash !e : boolean}$
  - $\vdash c : int$
  - $\dfrac{\vdash e_1 : int\quad \vdash e_2 : int}{\vdash e_1 + e_2 : int}$
  - $\dfrac{\vdash e_1 : boolean \quad \vdash e_2 : t \quad \vdash e_3 : t}{(e_1 ?
    e_2 : e_3) : t}$
    (define $t \Coloneqq boolean\mid int$)

## Implementation

- If the program type checks, return its type, otherwise throw an exception

```java
class TypeCheck extends DepthFirstVisitor {
  String visit(IntConst n) {
    return "int";
  }
  // f_0 and f_2 are the left and right subtrees, respectively
  String visit(Plus n) {
    String t_0 = n.f_0.accept(this);
    String t_2 = n.f_2.accept(this);
    if (t_0 == "int" && t_2 == "int") {
      return "int";
    } else {
      throw new Exception();
    }
  }
}
```

- All the variables' type information should be inside a symbol table (or type
  environment)
  - Basically just a table mapping variable identifiers to their types
  - The table is _not necessarily_ universal, because variables can go in/out of
    scope (try passing the table in as an argument to your `visit` function)
