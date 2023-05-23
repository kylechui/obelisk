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

## Abstract and Concrete Syntax

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
