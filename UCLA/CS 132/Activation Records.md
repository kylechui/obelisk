---
id: "Activation Records"
aliases:
  - "The Procedure Abstraction"
tags:
  - "CS132"
---

- In other words, "how to deal with the stack"

## The Procedure Abstraction

- We have a procedure $p$ calling a procedure $q$
- On entry, $q$'s environment should be established
- At a call, $q$'s environment should be preserved
- On exit, $q$'s environment should be torn down

## Activation Records

- Each procedure activation has an associated activation record (or stack frame)
- Responsibility is divided between the caller and callee
  - Caller (pre-call):
    - Allocate basic frame
    - Evaluate and store parameters
    - Store return address
    - Jump to child procedure
  - Callee (prologue):
    - Save registers, state
    - Store frame pointer
    - Set new frame pointer
    - Store static link
    - Extend basic frame (for local data)
    - Initialize locals
    - Fall through to code
  - Callee (epilogue):
    - Save registers, state
    - Store frame pointer
    - Set new frame pointer
    - Store static link
    - Extend basic frame (for local data)
    - Initialize locals
    - Fall through to code
  - Caller (post-call):
    - Copy return value
    - Deallocate basic frame
    - Restore parameters (if copy out)
