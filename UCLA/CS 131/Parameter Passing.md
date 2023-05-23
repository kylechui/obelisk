---
id: "Parameter Passing"
aliases:
  - "Positional vs. Named Parameters"
tags:
  - "CS131"
---

- Pass by value: The formal parameter is a copy of the original variable
- Pass by reference: The formal parameter refers directly to the original
  variable
- Pass by pointer: The formal parameter is a pointer that contains the address
  of the original variable

## Positional vs. Named Parameters

- Positional parameters must follow the order of the formal parameters
- Named parameters must match the name of the formal parameters
- Most languages let you specify default values for formal parameters, i.e. they
  are optional in the function call
  - In languages without mandatory argument labels, default parameters must be
    placed at the end of the parameter list
  - If they are mandatory, then you can use default values for any parameter
  - A few languages enable optional parameters without default values

## Variadic Functions

- They are functions that can take any number of values
