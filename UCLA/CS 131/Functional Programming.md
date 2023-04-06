---
id: "Functional Programming"
aliases:
  - "Comparisons with Imperative Programming"
tags:
  - "CS131"
---

- Every function _must_ take an argument
- Every function _must_ return a value
- Functions are _pure_ and have no side effects
  - They are said to exhibit
    [[Referential Transparency|referential transparency]]
  - Calling functions with the same inputs _always_ yields the same outputs
- All variables are _immutable_
- Functions are just like any other data, and can be stored in variables or
  passed around as arguments, i.e. they are _first-class_ objects

## Comparisons with Imperative Programming

- Imperative
  - Algorithmic: Series of statements
  - Changes in state are required
  - Multi-threading is bug-prone
- Functional
  - Transformation via function calls (recursion)
  - All variables are constant, no mutable state
  - Multi-threading is easy
    - Since there's no shared mutable state, there's no race conditions
    - Order of execution is of low importance, since there are no side effects
      - [[Haskell|Haskell]] is a **lazy language**, only evaluating expressions
        when necessary
