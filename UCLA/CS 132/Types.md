---
id: "Types"
aliases:
  - "Lambda Calculus"
tags:
  - "CS132"
---

- A _type_ is just a set of values, i.e. `int` refers to the set of integers in
  a programming language
  - Allows you to move error checking to compile time instead of runtime
    - Describe the set of all valid states in a program, and disregard invalid
      states
- The point of a [[Type Checking|type checker]] is to check the validity of
  programs that satisfy the grammar
  - First, check if the program is grammatically correct
  - Then, type check the program
  - Finally, run the program

## Lambda Calculus

- We define a grammar:
  - Numbers: $n$
  - Variables: $x$
  - Terms: $t\coloneqq x\mid t\quad t\mid t + t\mid t\cdot t\mid v$
    - The $t\quad t$ case represents function application
  - Values: $v\coloneqq \lambda x.t\mid n$
- Some rules (or judgements) for this grammar, where the numerator "evaluates
  to" the denominator:
  - $\dfrac{1}{n\Downarrow n}$
  - $\dfrac{1}{\lambda x . t\Downarrow \lambda x . t}$
  - $\dfrac{t_1\Downarrow v_1\quad t_2\Downarrow v_2}{t_1 + t_2\Downarrow v_1 +
    v_2}$
    - The first $+$ is a part of our grammar, while the second $+$ actually adds
      numbers together
  - $\dfrac{t_1\Downarrow v_1\quad t_2\Downarrow v_2}{t_1\cdot t_2\Downarrow v_1\cdot v_2}$
  - $\dfrac{t_1\Downarrow \lambda x.t_3 : [x\mapsto v_2]t_3\quad t_2\Downarrow v_3}{t_1t_2}$

## Typed Lambda Calculus

- $t\coloneqq x\mid \lambda x : T.t\mid t\quad t\mid True\mid False\mid t + t\mid
  if\ t\ then\ t\ else\ t$
- $T : bool\mid int\mid T_1\mapsto T_2$
  - $\dfrac{t_1 : int\quad t_2 : int}{t_1 + t_2 : int}$
  - $\dfrac{t_1 : bool\quad t_2 : T\quad t_3 : T}{if\ t_1\ then\ t_2\ else\ t_3 : T}$
- We have a mapping $\Gamma\colon var\to T$
  - Type checking a variable:
    - $\dfrac{(x:T)\in \Gamma}{\Gamma\vdash x : T}$
  - Type checking a function:
    - $\dfrac{\Gamma, (x : T_1)\vdash t : T_2}{\Gamma\vdash \lambda x : T_1\quad t : T_1\to T_2}$
  - Example:
    - $\dfrac{\Gamma, (x : int)\vdash x : int}{\Gamma\vdash \lambda x : int . x : int\to int}$
  - Type checking function application:
    - $\dfrac{\Gamma\vdash t_1 : T_{11}\to T_{12}\quad\Gamma\vdash t_2 : T_{11}}{\Gamma\vdash t_1\quad t_2 : T_{12}}$
- Some OCaml-ish syntax for defining a type checker:

```ocaml
type typ := Bool | Arrow of typ * typ
type t :=
  | True
  | False
  | Var of string
  | Function of string * typ * t (* input name, input type, output *)
  | FuncCall of t * t (* input, output *)
type env := (string * type) list (* variable id, type *)
  exception TypeError

let rec type_check (t : t) (env : env) : typ =
  match (t, env) with
  | (True, env) -> Bool
  | (False, env) -> Bool
  | (Var t, env) -> List.find (fun (x, _) -> x = t) env |> snd (* get first occurrence *)
  | (Function (x, t, b), env) -> Arrow (t, type_check b ((x, t) :: env))
  | _ -> raise TypeError
```

### Class Typing

- If we need to know about class $C$, look it up!
  - $\Gamma\vdash new\ D() : C$
  - A class type checks if all of its methods type check
    - Methods type check if the body of the method type checks
- For processing the `this` keyword, keep track of the class
  - $\Gamma, C\vdash this : C$
- $\dfrac{\Gamma, C\vdash e_1 : D\quad \Gamma\vdash e_2 : t_2}{\Gamma, C\vdash e_1.m(e_2)}$
- If an object of type $B$ is expected, and a child class $C$ is presented, that
  should still type check

### Subtyping

- $S <: T$ means any term of type $S$ can safely be used in a context where type
  $T$ is expected
  - "$S$ is a subtype of $T$"
  - For example, if class $C$ extends $D$, then $C$ is a subtype of $D$, or $C <: D$
- Some consequences:
  - $S <: S$ for all $S$
  - $\dfrac{S <: U\quad U <: T}{S <: T}$
  - $\dfrac{\Gamma\vdash t : S\quad S <: T}{\Gamma \vdash t : T}$
