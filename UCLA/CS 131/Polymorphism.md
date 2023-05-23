---
id: "Polymorphism"
aliases:
  - "Parametric Polymorphism: Templates"
  - "Parametric Polymorphism"
tags:
  - "CS131"
---

- Subtype polymorphism: A function is designed to operate on a supertype, and on
  all subtypes of that supertype
- Ad-hoc polymorphism: Define specialized versions of the same function for each
  type (overloading)
- Parametric polymorphism: A single function that can operate on many,
  potentially unrelated types

## Parametric Polymorphism

- Templates
  - Every time the function is called, the compiler generates a concrete version
    of the template function/class by substituting in the type parameter
- Generics
  - The generic code is compiled on its own, independent of its usages
  - When the compiler later compiles code that uses the generic, it will perform
    the type checking
  - We can limit generics to have certain behaviors via "bounding", using an
    interface
- Specialization: Defining a function for a specific type, e.g. for improved
  performance
