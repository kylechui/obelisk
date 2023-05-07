---
id: "Type Systems"
aliases:
  - "Strongly Typed Languages"
tags:
  - "CS131"
---

- Static type checking happens at compile time, while dynamic type checking
  occurs at runtime
  - In static typing, every variable must have a fixed type bound to it at
    compile time
- In a strongly typed language, all operations are guaranteed to only operate on
  the correct types, while in a weakly typed language there is no such guarantee
  - In a strongly typed language, there should _never_ be undefined behavior at
    runtime due to the type system
    - There is no possibility of an unchecked runtime type error
  - The language must be type-safe and memory-safe
  - For example, Javascript would be a strongly typed language because while it
    allows some strange behavior, it is all valid since the language does
    implicit conversion between types

## Strongly Typed Languages

- In general, the language should prevent operations on incompatible types or
  memory:
  - All of the operands must have compatible types
  - All conversions between types should be checked
  - Pointers are set to either point to `null` or a valid object at creation
  - Accesses to arrays and pointer arithmetic are bounds checked
  - Objects cannot be used after they are destroyed
- Memory safety is _required_ for a strong type system because otherwise one
  could access invalid memory (that may have some type) as if it were a
  different type

## Checked Casting

- A checked cast is a type-cast that results in an exception/error if the cast
  is illegal

## Weakly Typed Languages

- In general, the language does not necessarily prevent operations on
  incompatible types or memory
  - We can get undefined behavior at runtime!

## Reflection

- Type reflection is the process of querying a value's type

## Type Conversion and Casting

- A type $S$ is a _subtype_ of $T$ if:
  - $S$ takes on a subset of values that $T$ can
  - All operations that can be performed on a variable of type $T$ can also be
    performed on objects of type $S$
- For example, `float` is a subtype of `double`, `int` is a subtype of `const int`
- We perform type casts and conversions when we want to perform operations on
  the wrong type
  - Type conversion: A conversion that takes a value of type $S$ and creates a
    whole new temporary of type $T$ (with different memory, bit encodings, etc.)
  - Type casting: A cast takes a value of type $S$ and treats it as if it were
    a value of type $T$; no conversion takes place, no temporary is created
    - It is a different perspective on existing bits

## Three Categories of Casts and Conversions

- Explicit vs. Implicit
  - Whether or not you require explicit syntax in order to force the
    conversion/cast
    - Most explicit casts are "downcasts", from a supertype to a subtype
    - Turns a compile-time error into a runtime check
  - Implicit casts or implicit conversions (coercion) is one that occurs without
    explicit syntax
    - Most implicit casts are "upcasts", from a subtype to a supertype
    - Coercions from a subtype into a supertype are called type promotions
- Widening vs. Narrowing
  - Widening conversions/casts convert subtypes to supertypes
    - The value of the expression is preserved
  - Narrowing conversions/casts convert supertypes to subtypes, or to unrelated
    types
    - The value might lose some data
- Checked vs. Unchecked
  - Whether or not the casts/conversions are checked for compatible types
