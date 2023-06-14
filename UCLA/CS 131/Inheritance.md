---
id: "Inheritance"
aliases:
  - "Interface Inheritance"
tags:
  - "CS131"
---

- Inheritance is a technique where we define a new class based on an existing
  class or interface
- It allows us to:
  - Reuse code
  - Ensure that different classes behave in a standardised manner

## Interface Inheritance

- Creating many (potentially unrelated) classes that share a common interface
  - A class implements this interface by providing implementations of all of the
    functions in the interface
- How to use interface inheritance:
  - Define a public interface for a set of related methods
  - A derived class inherits the interface and provides implementations for the
    methods
- The interface specifies "what" should happen, while the derived class
  specifies "how" it should happen
- Classes can support (or implement) many interfaces
- Use when:
  - When you have a "can-support" relationship between a class and a group of
    behaviors
  - When you have different classes that all need to support the same behaviors,
    despite not being related
- This doesn't facilitate any code reuse

## Subclassing Inheritance

- A base class provides an interface and implementations
- The derived class inherits both the interface and implementations
  - It may also override or expand on the methods provided by the base class
- Use when:
  - When you have a "is-a" relationship, i.e. `Porsche` is a `Car`
  - When you expect the subclass to share the entire public interface and
    maintain the semantics of the super class' methods
  - When you can factor out common implementations into a superclass
- Results in poor encapsulation, because the derived class uses the base class'
  details
- Changes to superclasses can break all subclasses
  - Also known as the "fragile base class" problem

## Subclassing Alternative: Delegation

- A class embeds the original object as a member, and calls its functions
  directly
  - For example, a `Set` object contains a `Collection` object as a member, and
    calls its functions directly

## Implementation Inheritance

- Reusing the base class's method implementations (but the interface isn't
  necessarily exposed)
- This causes encapsulation issues
- The "derived" class isn't a subtype of the base class, since their
  relationship isn't public
- Delegation is almost always used instead

## Prototypal Inheritance

- Objects directly inherit from other objects
- Objects in JavaScript have a `__proto__` field that points to a parent object
  - You can change the `__proto__` to point to a different object, giving you
    inheritance

## Multiple Inheritance

- In general, multiple inheritance is an _anti-pattern_ and should not be used
- It leads to the _diamond pattern_, where two classes may inherit from the same
  base class and are inherited from by the same derived class
  - The most derived class could access a base field in multiple ways, causing
    race conditions at best and incorrect behavior at worst
- A good alternative is to inherit multiple _interfaces_
  - Even though the interfaces can specify the same function, implementing one
    function takes care of _both_ cases
  - It also allows for overloading, as there would be no ambiguity

## Inheritance and Typing

- Every time you define a class or interface, a new type is implicitly defined
  - Types associated with a concrete class are called _value types_
    - They can be used to define references, object references, pointers, and
      instantiate objects
  - Type associated with an interface or abstract class are called _reference
    types_
    - They can only be used to define references, object references, and
      pointers
- Subclass relationships have implied subtype relationships
- If a class implements an interface, the type of the class is a subtype of the
  type of the interface

## Subtype Polymorphism

- Subtype polymorphism is the ability to substitute an object of a subtype
  wherever an object of a supertype is expected
  - Methods of the subtype _should_ support the same _semantics_ as those of the
    supertype

## Dynamic Dispatch

- Dynamic dispatch is a runtime algorithm used to determine what method to call
  when an object calls a method
- Statically typed languages look at the class of the object to determine the
  right method to call
  - A virtual method table is used to point the names of virtual methods to
    their implementations
- Dynamically typed languages check if the target object has a matching method
  to call
  - A virtual method table is stored directly in the object itself, and is
    queried whenever a method is called
- Sometimes the method can be determined at compile-time via static dispatch
  - There is only one instance of the method, and no ambiguity
