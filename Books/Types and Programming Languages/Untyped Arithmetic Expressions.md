---
id: "Untyped Arithmetic Expressions"
aliases:
  - "Untyped Arithmetic Expressions"
tags:
  - "TaPL"
---

## Untyped Arithmetic Expressions

- We define a language using the following grammar:

```
t ::= true
    | false
    | if t then t else t
    | 0
    | succ t
    | pred t
    | iszero t
```

- We call `t` a "metavariable", since it is not a variable of the _object
  language_, but rather the _metalanguage_ (notation in which the description is
  given)
- Terms are phrases that represent computations, while expressions are used for
  all sorts of syntactic phrases
- No other constants are defined, since all other natural numbers can be derived
  from `0` via successive applications of `succ`

## Syntax

- An alternative form for the aforementioned grammar is the smallest set
  $\mathcal{T}$ satisfying:

  - $\{\texttt{true}, \texttt{false}, 0\}\subseteq \mathcal{T}$
  - If $t_1\in \mathcal{T}$, then $\left\{\texttt{succ }t_1, \texttt{pred }t_1,
    \texttt{iszero }t_1\right\}\subseteq \mathcal{T}$
  - If $t_1, t_2, t_3\in \mathcal{T}$ then $\texttt{if }t_1\texttt{ then
    }t_2\texttt{ else }t_3\in \mathcal{T}$

- We are defining $\mathcal{T}$ as a set of _trees_, not strings
- Alternatively, we may use the inference rule format to rewrite the above as
  follows:
  - $\texttt{true}\in \mathcal{T}$
  - $\texttt{false}\in \mathcal{T}$
  - $\texttt{0}\in \mathcal{T}$
  - $\dfrac{t_1\in \mathcal{T}}{\texttt{succ }t_1\in \mathcal{T}}$
  - $\dfrac{t_1\in \mathcal{T}}{\texttt{pred }t_1\in \mathcal{T}}$
  - $\dfrac{t_1\in \mathcal{T}}{\texttt{iszero }t_1\in \mathcal{T}}$
  - $\dfrac{t_1, t_2, t_3\in \mathcal{T}}{\texttt{if }t_1\texttt{ then
    }t_2\texttt{ else }t_3\in \mathcal{T}}$
- Rules with no premises are oftentimes called axioms

## Semantic Styles

- We need a precise definition of how terms are evaluated, i.e. the _semantics_
  of a language
- There are three basic approaches to formalizing semantics
  1. Operational semantics: Specify the behavior of a programming language by
     defining an _abstract machine_ for it
  2. Denotational semantics: The meaning of a term is taken to be a
     mathematical object
     - We find a collection of _semantic domains_ and then define an
       _interpretation function_ that maps terms into elements of these domains
     - It abstracts away from evaluation details and highlights essential
       concepts of the language
     - It is more powerful for reasoning about program behavior, i.e. showing
       that two programs behave the same, or that a program satisfies some
       specification
     - It is also easier to show that various situations are impossible in a
       language
  3. Axiomatic semantics: Instead of deriving laws from program behavior, the
     laws _are_ the definition of the language
     - The meaning of a term is what can be proved about it
     - It focuses attention on reasoning about programs, and has led to ideas
       like _invariants_
- Operational semantics used to be seen as much weaker, but is now the method of
  choice for defining programming languages and studying their properties

## Evaluation of Booleans

- We define the following rules for this language:
  - $E$-IfTrue: $\texttt{if true then }t_2\texttt{ else }t_3\to t_2$
  - $E$-IfFalse: $\texttt{if false then }t_2\texttt{ else }t_3\to t_3$
  - $E$-If: $\dfrac{t_1\to t_1'}{\texttt{if }t_1\texttt{ then }t_2\texttt{ else }t_3\to \texttt{if }t_1'\texttt{ then }t_2\texttt{ else }t_3}$
- The rules that govern how expressions get evaluated also implicitly set an
  evaluation order
  - For this language, we always evaluate the guard of an if-expression before
    its body
- We refer to $E$-If as a congruence rule, and $E$-IfTrue and $E$-IfFalse as
  computation rules
- Terms that cannot undergo any more evaluations are said to be in normal form
