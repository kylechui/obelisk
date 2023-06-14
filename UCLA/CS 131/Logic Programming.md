---
id: "Logic Programming"
aliases:
  - "Queries"
tags: []
---

- Prolog uses an _inference engine_
- Logic programming is a paradigm where we express programs as a set of facts,
  and a set of rules
  - We can then query the program, and Prolog will try and find a chain of
    connections between the query, facts, and rules that leads to an answer
- A fact is a predicate that declares an attribute of some atom, or a
  relationship between two or more atoms (or numbers)
  - They are _not_ function calls, but rather static assertions of different
    relationships (called functors)
- All functors and atoms _must_ be lowercase in Prolog!
  - Capital letters are used to denote variables
- A rule defines a new fact in terms of existing facts or rules
  - Each rule has two parts:
    - Head: Defines what the rule is trying to determine
    - Body: Specifies the conditions (or sub goals) that allow us to conclude
      that the head is true
- `,` in the body of a rule means "logical and"
- `:-` means "if"
- Rules can be recursive, and can have multiple parts
  - You define the base case first (top-to-bottom execution), and then any
    inductive cases
- Prolog operates on the _Closed World Assumption_, where statements that can be
  proven true are true, and all other statements are false

## Queries

- Prolog can answer two types of queries:
  - True/False questions
  - Fill-in-the blank questions (finds all possible matches)
    - Multiple unknowns are also possible
- The process of resolving a query (using facts and rules) is called
  _Resolution_

## Resolution

- We have a stack of goals and recursively:
  - Pop off the top goal and try matching it with every fact or rule in the
    database
  - If it matches with a rule, then add the preconditions in the body of the
    rule to a new goal stack, and bind any values to variables

## Unification

- Resolution _uses_ unification
- It is the process of:
  - Comparing the current goal with each fact/rule to see if they are a match
  - If they do match, Prolog maps variables to atoms
- How do we know if a goal matches a given fact or rule?
  - First, apply all current mappings to the goal
  - Then, treat the mapped goal and head of the fact/rule as trees
  - Then, compare the trees node-by-node
    - If both nodes are functors, make sure that the functors are the same and
      have the same number of children
    - If both nodes are atoms, make sure that the atoms are the same
    - Unmapped variables can match anything in the other tree
- Anytime you find an unmapped variable in one tree, map it to the value in the
  other tree
  - If both are unmapped, the mapping should be bidirectional

## Prolog Lists

- Lists can contain any value, including other lists
- Prolog uses a combination of pattern matching and unification to process lists
