---
id: "Interpreters"
aliases:
  - "Interpreters vs. Compilers"
tags:
  - "CS132"
---

- **Interpreter**: A program that directly executes program statements, without
  requiring them to be first compiled into machine language
  - The source file is loaded into memory
  - Necessary data structures get initialized
  - Keep running the program line by line until the program quits
    - Interpret the current statement
    - Update program state

## Interpreters vs. Compilers

|                    | Interpreter            | Compiler        |
| ------------------ | ---------------------- | --------------- |
| Lookup source code | At runtime             | At compile-time |
| Execute code       | Handled by interpreter | Left to runtime |

- Interpreters are necessarily slower than compilers because they must figure
  out additional computation at runtime that the compiler handles at
  compile-time
  - Unoptimized compilers are typically around an order of magnitude faster than
    their interpreter counterparts

## The JVM

- It has three components:
  - An interpreter
  - A fast compiler
  - A slow compiler
- When a file gets run:
  - It gets passed through the interpreter
  - The output is processed by the fast compiler
  - Then the code is ran for a short period of time
  - The code is then processed using the slow compiler, to try and produce
    better machine code

## Operational Semantics

- There are two kinds: small-step (like Sparrow) and big-step
- Suppose we have some grammar
  $$
  e\Coloneqq c \mid e + e \tag{$c$ is a constant value}
  $$
  - In small-step semantics, we use small _rules_ to describe the evaluation of
    an expression, i.e.
    $$
    \begin{align*}
      \frac{e_1\to e_1'}{e_1 + e_2\to e_1' + e_2} \\
      \frac{e_2\to e_2'}{e_1 + e_2\to e_1 + e_2'} \\
      c + c'\to c'' \tag{where $c'' = c + c'$ in math}
    \end{align*}
    $$
  - In big-step semantics, we use larger rules that go directly to values to
    describe evaluation, i.e.
    $$
    \begin{align*}
      \frac{e_1\to c\quad e_2\to c'}{e_1 + e_2\to c''} \tag{where $c'' = c + c'$ in math}
    \end{align*}
    $$
- Small-step semantics is typically better for evaluating infinite computation
- Big-step semantics somewhat abstract away the details of evaluation of the
  expression, focusing on the end result

## $\lambda$-calculus

- We describe the lambda-calculus via the grammar
  $$
  e\Coloneqq x\mid \lambda x.e\mid e_1\ e_2
  $$
- When interpreting a lambda $\lambda x. x + y + z$, $x$ is the argument to the
  lambda and $y, z$ are from the enclosing scope
  - Let $\varrho$ be a mapping from the environment and parameter names to
    values
  - Then we have
    $$
    \begin{gather*}
      \varrho\vdash x \to \varrho(x) \\
      \varrho\vdash \lambda x.e \to \langle \lambda x.e, \varrho \rangle \\
      \frac{\varrho\vdash e_1\to \langle \lambda x.e, \varrho'\rangle\quad \varrho'\vdash e_2\to v\quad \varrho'[x\mapsto v]\vdash e\to w}{\varrho\vdash e_1\ e_2\to w}
    \end{gather*}
    $$
    - On the second line, $\varrho$ captures the current values for $y, z$,
      forming a _closure_
