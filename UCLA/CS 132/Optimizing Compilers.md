---
id: "Optimizing Compilers"
aliases:
  - "Assignment"
tags:
  - "CS132"
---

- We approach compiler optimization through the lens of control-flow analysis
- Consider a method call `x.m()`
  - We are only able to figure out what to call because of types
  - Right now, we convert this into a sequence of machine instructions like
    `load, load, call`
    - Can we elide these loads? Can we inline the function and remove the call
      altogether?
- In a dynamically typed language, there was just a huge method table with class
  names for rows, and method names for columns
  - At runtime, the type of the value in `x` could be determined, and then the
    table could be queried
- Suppose $\Gamma\vdash x: B$, where $B <: A$ and $C, D <: B$, and both $A$ and
  $B$ have a method $m$
  - We call `B.m`, since it overrides `A.m`
  - This is accomplished via Class Hierarchy Analysis (CHA)
- We would like to _devirtualize_ this method call, by eliding the loads and
  directly calling the function
- Another approach is Rapid Type Analysis (RTA)
  - If we add a method `D.m`, then we must consider it because `x` could contain
    a `D` object, so how do we devirtualize?
  - One idea is to keep track of `new` calls, and if there are no `new D()`
    calls then we can devirtualize and know to call `B.m`
    - If there is a `new D()` in the code, then we can't devirtualize
- One question to consider is: What is the set of class names of the objects in
  `x`?
  - We can use constraint-based analysis:
    - From a program, we generate constraints
    - Solving the constraints, we get information about the program
- For every expression $e$, we define the _set variable of $e$_ by the range of
  set of class names for objects stored in $e$, and denote it by $[[e]]$
  - At different points throughout the program, $e$ could hold objects of
    varying types
  - Then we have $[[e]]$ is the set of all of these object types
- We want to find a superset (or as close as possible) to $[[e]]$, to guarantee
  correctness of our optimizer
- This is also called 0-CFA

## Assignment

- We know that $\texttt{new C()} = \left\{\texttt{C}\right\}$
- If we have an assignment `x = e;`, then we know that $[[x]]\supseteq [[e]]$
- This kind of analysis takes $\mathcal{O}(n^3)$ time
- Sometimes, the information gained from 0-CFA needs to be used to "refine" the
  type system, to allow for more aggressive inlining of functions
  - We call this Type-Safe Method Inlining (TSMI)
