---
id: "Object Oriented Programming"
aliases:
  - "Essential Components of OOP"
tags:
  - "CS131"
---

- Objects communicate with each other via messages (method calls)
  - They consist of implementations (code) and internal state (data)

## Essential Components of OOP

- Classes: A blueprint for making new objects
- Interfaces: A related group of function prototypes that we want a class to
  implement
- Object: Represents a particular "thing"
- Inheritance: Derived class inherits code/interface from a base class
- Subtype Polymorphism: Code designed to operate on an object of a supertype can
  also work on any object of a subtype
- Dynamic Dispatch: The code that gets executed depends on the target object and
  can only be determined at runtime
- Encapsulation: Bundling data and methods into a cohesive unit
  - Hide the implementation details from the user of the class, to force them to
    use the public interface
  - Programs are simpler, implementations can be updated in parallel, better
    modularity

## Classes

- Class definitions implicitly define new types

## Interfaces

- An interface is a related group of function prototypes that describes
  behaviors that we want one or more class(es) to implement
  - It specifies _what_ to do, not _how_
- We want this because there might be a set of classes that has common behaviors
  without common implementations to inherit
  - For example, finding the area of a shape
- Just like classes, interfaces implicitly define a new type called a reference
  type
  - Reference types can only be used to define pointers, references, but _not_
    objects
- The interface reference type is a supertype of any of the class types that
  implement it

## Objects

- Each object has its own copy of fields and methods
- Some OOP languages have objects but not classes

## Class Fields and Methods

- Sometimes we want the class itself to have a copy of a field/method
  - Defining class-level constants
  - Counting the number of objects
  - Assigning each object a unique ID
- Class fields in statically-typed languages are stored in the static data area
  of the process
- Class methods are only allowed to access class-level variables
- An initializer is different from a constructor in that it only runs _once_
  when the class is initialized, not every time an object is constructed

## Class Access Modifiers

- Public, Protected (accessible to subclasses), Private
