---
id: "Type Systems"
aliases:
  - "Types in Computer Science"
tags:
  - "TaPL"
---

## Types in Computer Science

- Formal methods are systems used to ensure that a system behaves correctly with
  respect to some specification of its desired behavior
  - They range in power, with the more powerful ones demanding more from
    programmers
  - One instance of lightweight formal methods is model checkers, which search
    for errors in finite-state systems
  - Type systems are the most prominent form of lightweight formal methods
    - Lightweight: Can be built into compilers, static analysis tools, etc.
- Type systems are a syntactic method for proving the absence of certain program
  behaviors, by classifying phrases by the kinds of values they compute
  - Can be thought of as statically computing an approximation of the program's
    runtime behavior
  - They are necessarily conservative
    - Type systems prove the _absence_ of bad programs, but cannot prove their
      presence, and so inevitably must reject some valid programs
  - These undesirable behaviors are called run-time type errors
  - They enforce higher-level modularity properties, and preserve the validity
    of user-defined abstractions
