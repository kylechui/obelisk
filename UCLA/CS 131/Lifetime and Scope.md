---
id: "Lifetime and Scope"
aliases:
  - "Lexical Scoping"
tags:
  - "CS131"
---

- Every variable and value has a _lifetime_, over which they are valid and may
  be accessed
  - It is possible for a value to be "alive", but still inaccessible
  - A variable and the value that it points to can also have different
    lifetimes!
    - Consider a pointer to some object that is also referenced elsewhere; the
      pointer might "die" first but the object will live on as long as it is in
      use somewhere
- A variable is _in scope_ in some part of a program if it can be explicitly
  accessed by name in that region

## Lexical Scoping

- More or less what you're used to: if the variable is not found in the current
  context, search upwards through the enclosing context until you hit the global
  context
- This is sometimes referred to as the LEGB rule
  - Local scope: Typically a function, block, expression, etc.
  - Enclosing scopes: Scopes that contain the current local scope
  - Global scopes:
  - Built-in scope: Includes built-in keywords and constants
- When a variable is defined inside an inner context, lexical scoping languages
  use an approach called _shadowing_
  - The redefined variable takes precedence over the outer context variable
  - After the inner context is finished, we resume to using the outer context
    variable

## Dynamic Scoping

- The value of a variable takes on the most recently defined version, regardless
  of lexical scope
  - What matters is the _chronological order_ that variables are defined in
- Very few languages still use this strategy, one of the remaining ones is Emacs
  Lisp
