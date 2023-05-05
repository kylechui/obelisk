---
id: "Intermediate Representation"
aliases:
  - "Sparrow's Grammar"
tags:
  - "CS132"
---

## Sparrow's Grammar

- Program: $p\Coloneqq F_1\dotsc F_m$
- Function declaration: $F\Coloneqq func\ f(id_1\dotsc id_f)\ b$
- Block: $b\Coloneqq i_1\dotsc i_n\ return\ id$
- Instruction:
  $$
  \begin{aligned}
    i\Coloneqq \ell\colon &\mid id = c \\
    &\mid id = @f \\
    &\mid id = id + id \\
    &\mid id = id < id \\
    &\mid id = [id + c] \\
    &\mid [id + c] = id \\
    &\mid id = id \\
    &\mid id = alloc(id) \\
    &\mid id = print(id) \\
    &\mid id = error(s) \\
    &\mid id = goto(\ell) \\
    &\mid id = if\ 0\ id\ goto\ \ell \\
    &\mid id = call\ id(id_1\dotsc id)
  \end{aligned}
  $$
  - $c$ is an integer literal
  - $@f$ is a pointer to $f$
  - $[x]$ refers to the heap address at $x$
