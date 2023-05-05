---
id: "Operational Semantics"
aliases: []
tags:
  - "CS132"
---

- Answering the question "what does my program do?"
- Helps us improve the quality of tooling
- Program state: $(p, H, b^\bullet, E, b)$
  - $p$ is the whole program
  - $H$ is the heap
  - $b^\bullet$ is the block of the current function
  - $E$ is the environment; maps from ids to values
  - $b$ is the set of instructions left in the block
- Upon each instruction, we map
  $$
  (p, H, b^\bullet, E, b)\to (p, H', b^{\bullet'}, E', b')
  $$
  - Execution flow just hops from state to state
    $$
    \begin{aligned}
    (p, H, b^\bullet, E, \ell:\quad b)&\to (p, H, b^\bullet, E, b) \\
    (p, H, b^\bullet, E, id = c\quad b)&\to (p, H, b^\bullet, E\cdot [id\mapsto c], b) \\
    (p, H, b^\bullet, E, id = @f\quad b)&\to (p, H, b^\bullet, E\cdot [id\mapsto f], b) \\
    (p, H, b^\bullet, E, id = id_1 + id_2\quad b)&\to (p, H, b^\bullet, E\cdot [id\mapsto (c_1 + c_2)], b) \\
    (p, H, b^\bullet, E, id = id_1 < id_2\quad b)&\to (p, H, b^\bullet, E\cdot [id\mapsto c_1 < c_2], b) \\
    (p, H, b^\bullet, E, id = [id + c]\quad b)&\to (p, H, b^\bullet, E\cdot [id\mapsto (a_1, c_1 + c)], b) \\
    \end{aligned}
    $$
    - The square bracket notation indicates that $id$ is either initialized with
      value $c$, or has its value updated to $c$
    - It is assumed that $E(id_1) = c_1$ and $E(id_2) = c_2$ (both integer
      literals)
      - The heap address case is similar; if $E(id_1) = (a_1, c_1)$ and $E(id_2)
        = c_2$, then our new environment is $E\cdot [id\mapsto (a_1, c_1 +
        c_2)]$
    - For heap access, we need to make sure that the new index $c + c_1$ is
      within the domain of the heap
