---
id: "Encapsulation"
aliases:
  - "Properties, Accessors, and Mutators"
tags:
  - "CS131"
---

- Ideally, hide all implementation details from all other classes
- Make all member fields, constants, and helper methods private
- Avoid providing implementation-specific getter/setter functions

## Properties, Accessors, and Mutators

- A property is an attribute of an object
  - Use this over a method when you're exposing the state of a class, or some
    minor computation
  - Use methods for more complex behaviors that require heavy computation
- An accessor is a method that retrieves the value of a property
- A mutator is a method that mutates the value of a property
