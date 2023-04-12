---
id: "Java Compiler Compiler"
aliases:
  - "Java Tree Builder"
tags:
  - "CS132"
---

- It can be written in any language, but is written in Java
- It is based on LL(k) instead of LALR(1)
- Grammars are written in EBNF
  - It transforms a grammar into an LL(k) parser
- The grammar can have embedded action code
- Input format
  - One file that contains a header, token specifications for lexical analysis,
    and grammar

```c
javacc fortran.jj // Generates parser with the specified name
javac Main.java // Main.java contains a call of the parser
java Main < prog.f // Parses the program prog.f
```

- The visitor pattern
  - In OOP, the visitor pattern enables you to add a new operation to an
    existing structure without changing the classes of the objects
  - There are two requirements:
    - The set of classes must be fixed in advance
    - Each class must have an accept method
  - A form of "double dispatch", where you have mutual recursion via `visit` and
    `accept` calls

## Java Tree Builder

- Transforms a JavaCC grammar into three components:
  - A JavaCC grammar with embedded code for building a syntax tree
  - One class for every form of tree node
  - A default visitor that can do DFS of a syntax tree

```c
jtb fortran.jj // Generates jtb.out.jj
javacc jtb.out.jj // Generates parser with the specified name
javac Main.java // Main.java contains a call of the parser, calls to visitors
java Main < prog.f // Builds syntax tree for prog.f, executes the visitors
```
