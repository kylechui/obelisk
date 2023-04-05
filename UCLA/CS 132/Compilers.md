---
id: "Compilers"
aliases:
  - "Abstract View"
tags:
  - "CS 131"
  - "CS 132"
---

- **Linker**: A program that combines multiple object modules and libraries into
  a single executable file or library
- **Compiler**: A program that translates program source into object modules
  (which are either machine language, or bytecode targeted at an interpreter)
  - The lexical analyzer (including [[Scanners|scanners]]) breaks the source
    into a list of tokens
  - The parser uses the grammar of the language to validate the
    [[Syntax|syntax]], then converts the tokens into an abstract syntax tree
  - The semantic analyzer checks the [[Semantics|semantics]] validity of the
    tree, and produces an annotated parse tree
  - The intermediate representation generator creates an abstract representation
    of the program (independent of the original language)
  - The code generator then converts the intermediate representation into
    machine code or bytecode
- Machines are constantly changing, so we need new compilers to deal with the
  new architectures
  - Similarly, changes in compilers should prompt changes in architecture,
    yielding new languages and features
- Ideal properties for compilers:
  - Correct code (focus of this course!)
  - Output runs fast
  - Compiler runs fast
  - Compile time proportional to program size
  - Support for separate compilation
  - Good diagnostics for syntax errors
  - Works well with debugger
  - Good diagnostics for flow anomalies
  - Cross language calls
  - Consistent, predictable optimization

## Abstract View

- Compilers should:
  - Recognize legal (and illegal) programs
  - Generate correct code
  - Manage storage of all variables and code
  - Agree on format for object (or assembly) code
- A two-pass compiler has:
  - An intermediate representation (IR)
  - Has a [[Front End|front end]] and [[Back End|back end]]
    - Or even multiple front ends!
  - Multiple passes should yield better code

## Optimizing Compilers

- The optimizer analyzes and changes the IR to reduce runtime, while preserving
  values
- Nowadays typically implemented in multiple passes
  - Each pass can perform:
    - Constant propagation and folding
    - Code motion
    - Reduction of operator strength
    - Common sub-expression elimination
    - Redundant store elimination
    - Dead code elimination
