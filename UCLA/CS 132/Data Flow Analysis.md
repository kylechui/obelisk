---
id: "Data Flow Analysis"
aliases:
  - "Liveness Analysis and Copy Propagation"
tags:
  - "CS132"
---

- Copy propagation: We wish to see if we can elide unnecessary copies wherever
  possible
- Consider the following code:
  ```
  b = a
  c = b
  d = b
  ```
  - We can elide the first assignment, by substituting all uses of `b` with `a`
    - After the substitution, we perform _dead code elimination_ via liveness
      analysis to remove the first assignment
- We can visualize these assignments as a control flow graph, where we keep
  track of the last assignment to `b` and have directed edges to the other two
  statements
  - We would also like all paths from start to finish to pass through the node
    `b = a`, otherwise `b` could potentially be uninitialised

## Liveness Analysis and Copy Propagation

|                | Liveness Analysis                                 | Copy Propagation                                                      |
| -------------- | ------------------------------------------------- | --------------------------------------------------------------------- |
| Key concepts   | def, use, in, out                                 | gen, kill, in, out                                                    |
| Variables      | range over sets of variables _that are live_      | range over copy statements _that we can use to transform our program_ |
| Style          | backwards                                         | forwards                                                              |
| Out constraint | $$out[n] = \bigcup_{s\in \mathrm{succ}(n)}in[s]$$ | $$out[n] = gen(n)\cup (in[s]\setminus kill[n])$$                      |
| In constraint  | $$in[n] = use(n)\cup (out[n]\setminus def(n))$$   | $$in[n] = \bigcap_{p\in pred(n)}out(p)$$                              |

- The concepts in, out for both columns are the variables that represent the set
  of valid variables, statements
- The in constraint for copy propagation uses intersection instead of union
  because we only wish to substitute if all previous nodes have `b = a`
  - If this is not the case, then substitution doesn't make sense, since the
    value of `b` in the path that doesn't contain `b = a` would be clobbered by
    the value of `a`
- When does a statement `s` kill `b = a`?
  - When `s` assigns to `b` or `a`
- The time complexity of both analyses is roughly $\mathcal{O}(n^4)$

## Example

|         | gen     | kill             | in  | out     | in      | out              |
| ------- | ------- | ---------------- | --- | ------- | ------- | ---------------- |
| `b = a` | `b = a` | `c = b`, `d = b` | N/A | `b = a` | N/A     | `b = a`          |
| `c = b` | `c = b` | N/A              | N/A | `c = b` | `b = a` | `c = b`, `b = a` |
| `d = b` | `d = b` | N/A              | N/A | `d = b` | `c = b` | `c = b`, `d = b` |
