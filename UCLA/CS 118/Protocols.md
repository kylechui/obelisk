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
- Transport layer protocol: Handles delivery reliability, multiplex within a
  host, i.e. TCP or UDP
  - It doesn't know/care about which paths data takes through the network
  - Different transport protocols exist for different purposes (i.e.
    reliability, congestion control, [[Network Performance|performance]], etc.)
- Network layer protocol: Forwards packets from source to destination, i.e. IP
  - Very hard, as there are many different parties involved (client, ISP,
    server, etc.)
- Link layer protocol: Transfers data between adjacent network elements, i.e.
  ethernet, WiFi
  - Different mediums require a different link layer protocol
- Physical layer: "Bits on the wire"
