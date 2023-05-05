---
id: "Application Layer Protocols"
aliases:
  - "Addressing Processes"
tags:
  - "CS118"
---

- Typically it's not software pieces that are communicating with one another,
  but rather processes (programs running within an end system)
  - They communicate by sending messages across a computer network
  - Networking applications have application-layer protocols that define the
    format and order of the messages exchanged between processes, as well as
    actions taken before/after transmission/receipt of a message
- Only a piece of a network application
- The host that initiates the session is labeled the client

## Addressing Processes

- The destination host is specified by its IP address
  - The port number is also necessary to send a message to the right process
- The _user agent_ is an interface between the user and network application
  - For example, the user agent for the internet is a browser

## What Services Does an Application Need?

- We can classify an application's service requirements along three dimensions:
  - Data loss: Some important applications require that no data is lost during
    a message transfer, while other applications can tolerate a small amount of
    data loss
  - Bandwidth: Some applications require 100% of their bandwidth in order to
    function properly
  - Timing: Real-time services like video calling have very tight constraints on
    what constitutes "effective" message transfer
