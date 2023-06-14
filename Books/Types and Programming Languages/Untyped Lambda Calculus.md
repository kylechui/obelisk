---
id: "Untyped Lambda Calculus"
aliases:
  - "The Basics"
tags:
  - "TaPL"
---

- A complex programming language can be understood by formulating it as a tiny
  core calculus
  - This language is lambda-calculus, where all computation is described via
    function definition and application
- Lambda-calculus can simultaneously be viewed as:
  - A simple programming language that describes computations
  - A mathematical object about which statements can be proved
- Lambda-calculus can then be extended via concrete syntax for a variety of
  features, eventually leading to languages like ML and Haskell

## The Basics

- Procedural (or functional) abstraction allows us to write a procedure that
  performs a computation generically, instead of writing the same calculation
  over and over
- We use $\lambda x.t$ to denote a function that takes in $x$ as an argument,
  and yields $t$ as a result (which may or may not depend on $x$)
- The syntax of the lambda-calculus can be defined as follows:

$$
\begin{align*}
  t &\Coloneqq x \tag*{Variable} \\
    &\mid \lambda x.t \tag*{Abstraction} \\
    &\mid t t \tag*{Application}
\end{align*}
$$

### Abstract and Concrete Syntax

- Concrete syntax refers to strings of characters that programmers read and
  write
- Abstract syntax is a simpler representation of the program as a labeled tree
  (also known as an _abstract syntax tree_ or _AST_)
  - This representation makes the structure of the terms more obvious
- The transformation from concrete to abstract syntax is done in two steps:
  - The lexical analyzer converts the input string to a sequence of tokens
    - It also removes comments, and deals with white space, etc.
  - The parser transforms the sequence of tokens into an AST
    - It handles operator precedence, encoding it directly into the structure of
      the tree
- By convention, function application is left-associative and the bodies of
  abstractions extend as far right as possible

### Scope

- A variable $x$ is said to be _bound_ if it occurs in the body $t$ of an
  abstraction $\lambda x.t$
  - It is _free_ if it is not bound by an enclosing abstraction
- A term with no free variables is _closed_, also called a _combinator_
  - For example, the identity function $\lambda x.x$ is a combinator

### Operational Semantics

- Lambda-calculus has no primitives, just functions and function application
- Each step in our computation consists of rewriting an application by
  substituting the right hand components for the bound variable in the body of
  the abstraction
  - This can be written as:
    $$
    (\lambda x.t_{12}) t_2\to [x\mapsto t_2]t_{12}
    $$
  - Terms of this kind are called _redexes_ (reducible expressions)
  - This method of rewriting the redex is called a _beta-reduction_
- There are a few strategies for evaluating redexes:
  - Full beta-reduction: Any redex can be reduced at any time
  - Normal order: The leftmost, outermost redex is reduced first
  - Call by name: Same as normal order, but no reductions are allowed inside
    abstractions
    - Haskell uses a modified version of this called "call by need", which
      memoizes previous computations
      - This results in a abstract syntax _graph_, instead of _tree_, as there
        can be some sharing in the computation of terms
  - Call by value: Outermost redexes are reduced first, and a redex is only
    reduced if its right-hand side has already been reduced to a value
    - Basically a function is only applied if all of its arguments have already
      been reduced
    - This is known as _strict_ evaluation

## Programming in Lambda-calculus

### Multiple Arguments

- There are no multi-argument functions, but it can be emulated via higher-order
  functions
  - The function $\lambda(x,y).s$ can be transformed into $\lambda x.\lambda
    y.s$
  - In general, $n$-argument functions can be transformed into the composition
    of $n$ single-argument functions, via a process known as _currying_

### Church Booleans

- We can encode booleans in the lambda calculus via:
  $$
  \begin{align*}
    \texttt{tru} &= \lambda t.\lambda f.t \\
    \texttt{fls} &= \lambda t.\lambda f.f
  \end{align*}
  $$
  - Here we see that $\texttt{tru}$ just selects the first of its two arguments,
    and $\texttt{fls}$ selects the last
- With this we can define some other boolean functions:
  $$
  \begin{align*}
    \texttt{and} &= \lambda b.\lambda c. b\ c\ \texttt{fls} \\
    \texttt{or} &= \lambda b.\lambda c. b\ \texttt{tru}\ c \\
    \texttt{not} &= \lambda b.b\ \texttt{fls tru}
  \end{align*}
  $$
  - For example, with a little stamina one can evaluate:
    $$
    \begin{align*}
      \texttt{and tru tru} &= \texttt{tru tru fls} \\
                           &= \texttt{tru}
    \end{align*}
    $$
  - Furthermore:
    $$
    \begin{align*}
      \texttt{and fls tru} &= \texttt{fls tru fls} \\
                           &= \texttt{fls}
    \end{align*}
    $$

### Pairs

- We can use booleans to encode pairs of values as follows:
  $$
  \begin{align*}
    \texttt{pair} &= \lambda f. \lambda s. \lambda b. b\ f\ s \\
    \texttt{fst} &= \lambda p. p\ \texttt{tru} \\
    \texttt{snd} &= \lambda p. p\ \texttt{fls}
  \end{align*}
  $$
  - We verify:
    $$
    \begin{align*}
      \texttt{snd}\ (\texttt{pair}\ v\ w) &= (\texttt{pair}\ v\ w)\ \texttt{fls} \\
                                          &= \texttt{fls}\ v\ w \\
                                          &= w
    \end{align*}
    $$

### Church Numerals

- We can define $\mathbb{Z}_{\geq 0}$ via
  $$
  \begin{align*}
    c_0 &= \lambda s.\lambda z.z \\
    c_1 &= \lambda s.\lambda z.s\ z \\
    c_2 &= \lambda s.\lambda z.s\ (s\ z)
  \end{align*}
  $$
- Here we have that $s$ behaves like a "successor" function, which returns the
  next whole number, and $z$ behaves like the constant 0
- The actual successor function can be defined via
  $$
  scc = \lambda n. \lambda s.\lambda z. s\ (n\ s\ z)
  $$
  - Alternatively, this also works:
    $$
    scc = \lambda n. \lambda s.s\ n
    $$
