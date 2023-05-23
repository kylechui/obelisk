---
id: "Error Handling"
aliases:
  - "Handling Paradigms"
tags: []
---

- A bug is a flaw in the program's logic
- An unrecoverable error is a non-bug error where recovery is impossible and the
  program must shut down
- A recoverable error is a non-bug error where recovery is possible and the
  program may continue executing
- A result is an indication of the outcome/status of an operation

## Handling Paradigms

- Do it yourself: Programmer provides their own way of handling errors, i.e.
  defining custom result types
- Error objects: Error objects are used to return an explicit error from a
  function to its caller
- Optional object: Used to return a single result that represents either a valid
  value or generic failure condition
- Result object: Returns a single result that represents a value or a specific
  error object
- Assertions/conditions: Checks whether a required condition is true, and exits
  the program if not
- Exceptions/panics:

## Error Objects

- Specific objects that are independent of any valid return value
- Error objects are provided by the language as a class
  - They are returned along with a function's result as a separate return value

## Optionals

- An optional returns a single result that represents a valid value or a generic
  failure

## Result Object

- A single result that either represents a valid value or distinct error

## Assertions

- We use assertions for validating:
  - Preconditions: Something that must be true before a function call
  - Postconditions: Something that must be true after a function call
  - Invariant: A condition that should be true across a function or class's
    execution

## Exception Handling

- Used for bugs, unrecoverable errors, and recoverable errors
- Error checking makes the logic of your code harder to understand
  - Exception handling separates the handling of exceptional states from core
    logic
- There's a catcher and a thrower
  - The catcher consists of:
    - A block of code that attempts some number of operations that might result
      in an unexpected error
    - The exception handler runs if and only if an error occurs, and handles the
      error
  - The thrower consists of:
    - A function that performs an operation that might result in an error
    - If an error occurs, the thrower creates an exception object and "throws"
      it to the exception handler
- A _panic_ is an exception that can't be caught, and that crashes the program
- Some languages have a third component used to guarantee certain operations
  - In Java, it's called the "finally block"

## Exception Handling Guarantees

- Failure transparency (no-throw): A function guarantees that it will not throw
  an exception, and called functions will handle exceptions internally
- Strong exception guarantee: If a function throws an exception, the program
  state will be rolled back to what it was prior to the function call
- Basic exception guarantee: Exceptions will leave the program in a valid state,
  i.e. no resources are leaked and all invariants are intact

## Panics

- A panic is used to abort execution due to an exceptional situation
  - Think of it as an uncaught exception, without anything being handled
    (program immediately terminates)

## Error Handling Best Practices

- Use assertions
  - Checking for errors that should never occur, e.g. invalid invariants
- Use optionals or error/result object
- Use optionals or error/result object
- Use exceptions
- Use panics
