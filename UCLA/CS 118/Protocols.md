---
id: "Protocols"
aliases:
  - "Internet Protocol Stack"
tags:
  - "CS118"
---

- A format for sending and receiving messages
  - Includes the order of packets sent and received, as well as the actions
    taken on packet transmission and reception

## Internet Protocol Stack

- The protocol stack is like a set of nested envelopes, embodying the separation
  of concerns
- Application layer protocol: Supports data exchange between application
  processes, i.e. smtp, http, DNS
  - Doesn't care _how_ data is sent; assumes it can be sent reliably
  - Only concerned with the _presentation_ of the message
  - It decides where messages should be delivered to, where the receiver is
    identified by a name (which gets translated into an IP address)
- Transport layer protocol: Handles delivery reliability, multiplex within a
  host, i.e. TCP or UDP
  - It doesn't know/care about which paths data takes through the network
  - Different transport protocols exist for different purposes (i.e.
    reliability, congestion control, [[Network Performance|performance]], etc.)
  - Only concerned with delivering some data to the destination, identified by
    an IP address and (trans)port number
  - The network is unreliable; packets can be garbled, lost, or reordered
- Network layer protocol: Forwards packets from source to destination, i.e. IP
  - Very hard, as there are many different parties involved (client, ISP,
    server, etc.)
  - It sends data segments _towards_ the destination, without looking beneath
    the IP level (actual data)
- Link layer protocol: Transfers data between adjacent network elements, i.e.
  ethernet, WiFi
  - Different mediums require a different link layer protocol
- Physical layer: "Bits on the wire"
- Each protocol puts only _necessary_ information into the **protocol header**,
  so each layer only sees the bare minimum amount of information necessary to
  perform its job

## Why Five Layers?

- Two layers are taken as given (different application protocols, hardware)
  - The remaining layer(s) span the two, and are commonly referred to as the IP
    layer(s)
- The transport layer adapts what IP offers to what applications want
- The link layer adapts what the hardware offers to what IP wants
