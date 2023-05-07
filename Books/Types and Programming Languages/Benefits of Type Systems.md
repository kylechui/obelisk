---
id: "Benefits of Type Systems"
aliases:
  - "Error Detection"
tags:
  - "TaPL"
---

## Error Detection

- Errors that are detected early can be fixed immediately
- Errors can often be pinpointed more accurately during type checking than
  runtime
  - Runtime errors may not be visible until some time after things begin to go
    wrong
- It also helps guide refactorings, since changing the declaration of a datatype
  will make all references to it type-inconsistent, and the programmer can
  simply go through all the resulting errors

## Abstraction

- Type systems enforce disciplined programming
  - They form the backbone of _module languages_ that integrate large systems
- Interfaces can be viewed as "types of modules", summarizing the facilities
  provided by the module
- Module-based systems tend to have better abstractions and separation between
  interface and implementation

## Documentation

- Types can give hints about a program's behavior
- They can be thought of as compiler-enforced comments, and can never become
  outdated

## Language Safety

- A safe language is one that protects its own abstractions
  - Safety refers to the ability of a language to guarantee the integrity of the
    abstractions it provides over machine services
- In unsafe languages, it is necessary to keep in mind low-level details (i.e.
  layout of data in memory, order of allocation, etc.)
  - Programmers cannot take advantage of the abstractions provided by the
    language
- This is different from type safety, although it can be achieved via type
  checking
- Unsafe languages provide "best effort" static type checkers that can help
  eliminate the most obvious bugs
  - They can suggest the presence of run-time type errors, but cannot prove
    their absence
- There are no dynamically checked, unsafe languages
  - Once _most_ operations are checked at runtime, there is little cost to
    checking _all_ operations at runtime

## Efficiency

- By providing type information, the computer can use different bit
  representations for different values, optimizing computations
- In safe languages, dynamic checks at runtime can be eliminated by proving
  those invariants statically
