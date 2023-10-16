---
id: "Software Deployment Issues"
aliases: []
tags:
  - "Nix"
---

- The goal for [[Software Deployment|software deployment]] should be:
  - For given inputs, the software on an end-user's machine should have
    identical behavior as on the developer machine
- We call deployments "correct" if they are _complete_ and components _do not
  interfere_ with one another
  - Completeness means that all dependencies exist
  - Interference occurs when multiple software components occupy the same
    namespace, making it impossible to distinguish between them
- There are two broad categories of issues preventing distribution from being as
  simple as "copy the files over"

## Environment Issues

- The program may demand that certain properties are satisfied by its
  environment
  - Dependencies: Configuration files, other programs, OS properties, etc.
- It is hard to test for a full dependency specification; we often find out
  about missing dependencies on the end-user machine
- There are multiple sets of dependencies that may not be the same, i.e.
  runtime, compile-time, testing-time
- Dependencies must be compatible with one another, and should try to avoid the
  [[Diamond Problem|diamond problem]]
- Components can depend on _hardware_, which can only be checked and not
  realized
- Deployment can be a distributed problem, where the dependencies could be on
  different machines, networks, etc.

## Manageability Issues

- We wish to manage basic operations on our system, i.e. packaging,
  transferring, installing, upgrading, removing, querying, etc.
  - We wish to support the _evolution_ of our system over time
- Uninstallation should not remove packages that are still in use by other
  programs
- When downgrading, we must take care not to modify anything that would degrade
  other non-related packages
  - This sometimes leads to _bit rot_, when stuff that initially worked now
    fails due to changes in the environment
- Administrators often want to query properties of the system, e.g. size
- We want to be able to roll back changes if an upgrade causes some failure
