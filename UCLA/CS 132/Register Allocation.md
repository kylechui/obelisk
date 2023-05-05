---
id: "Register Allocation"
aliases:
  - "Register Allocation"
tags: []
---

- The problem is that Sparrow has an unbounded number of variables that should
  be "equally accessible"
- When we compile down to RISC-V, we only have a finite number of registers, so
  only a finite amount of "fast" storage
  - This question extends to other kinds of memory, like L1 or L2 cache
- We are left with two questions:
  - Can we fit all of our variables into the registers such that we have "fast"
    access to all of them?
  - If not, which ones should we put into the registers

## Register Allocation

- The solution is _register allocation_, which is an algorithm for answering
  these two questions, and it proceeds in two phases:

1. Liveness analysis
   - This is done using an interference graph
2. Graph coloring

## Motivating Example

- Consider the following code, with two registers $r_1, r_2$:

```python
a = 1        # r1 = 1
b = 2        # r2 = 2
c = a + 3    # [s + 0] = r1 + 3
print b + c  # ???
```

- We might need "reserve" registers in case some of the values we need are
  stored in memory
  - If we have multiple values in memory, we need more than one reserve
    register

## Liveness Analysis

- A variable is "live" if we need to use it later, i.e. it is "live" from its
  first assignment to its last usage
  - If multiple variables are live at the same time, then they should live in
    different locations, otherwise one would clobber the other
  - A variable isn't "live" for its last usage because at that point in time we
    can overwrite the contents of that register immediately after reading its
    contents
- We construct an _interference graph_:
  - The nodes are our program variables, and the edges are overlapping live
    ranges
- In the example from before, we have edges `a-b-c`
  - We can then think of our registers as different colors, and then our
    register allocation problem turns into a graph coloring problem

## A More Difficult Example

```python
               # Live variables:
a = 1          # a,
b = 10         # a, b
c = 9 + a      # b, c
d = a + c      # b, c, d
e = c + d      # b, e
f = b + 8      # e, f
c = f + e      # c, e
f = e + c      # c, f
b = c + 5      # b, f
return b + f   #
```

- We also need a graph for the control flow of the program, i.e. if we have an
  if-else statement in our program
- Also note that in the middle of the program, we can free up the space that $b$
  used because the next "usage" is actually an assignment
  - We use a new heuristic of "liveness" where a variable is live from
    assignment until the last usage _before the next assignment, if any_
- The number of registers we need to avoid "spillage" is the degree of the
  maximum clique in the graph
  - For a clique of degree $n$, we _need_ $n$ registers because we constantly
    need all nodes/registers simultaneously
  - All other variables can then be stored in some other register that gets
    overwritten before "entering" the clique, or overwrites some member of the
    clique after "exiting"
- We use the notation:
  - `def[n]` refers to the variables assigned in $n$, where $n$ is a statement
  - `use[n]` refers to the variables used in $n$, where $n$ is a statement
  - `in[n]` refers to the variables that are live coming into $n$
  - `out[n]` refers to the variables that are live going out of $n$

## Liveness Equations

- We get the equations:
  - The variables in use coming out of a statement is the union of all variables
    in use going into any of the current statement's successors:
    $$
    out[n] = \bigcup_{s\in \mathrm{succ}(n)}in[s]
    $$
  - hello
    $$
    in[n] = use[n]\cup (out[n]\setminus def[n])
    $$
- We can solve these via an iterative algorithm
  - Fixed-point solution: Initialize all $in[n] = \varnothing, out[n] =
    \varnothing$
  - Then go through and apply the rules outlined above
  - Once there are no more changes between iterations, we are done and we use
    `in[n]` as our final register allocation
