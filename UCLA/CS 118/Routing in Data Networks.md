---
id: "Routing in Data Networks"
aliases:
  - "Virtual Circuit Networks"
tags:
  - "CS118"
---

- There are two broad classes of [[Packet Switching|packet switched networks]]:
  datagram networks and virtual-circuit networks
  - Datagram networks route packets according to destination addresses
  - Virtual-circuit networks route packets according to virtual-circuit numbers

## Virtual Circuit Networks

- A virtual circuit consists of:
  - A path between the source and destination
  - Virtual circuit numbers (labels for each link along the path)
  - Entries in VC-number translation tables in each router along the path
    - The packet adopts the number of the link that it is about to go through
- VC-numbers are relative to the circuit; otherwise, there would need to be a
  lot more communication for links to agree on numbers
- The network routers must maintain state information for the ongoing
  connections
  - Every time a new connection is established, an entry must be added to the
    VC-number translation table
  - Each time a connection terminates, an entry must be released from the table

## Datagram Networks

- The address of the destination is ordered hierarchically
  - Each router looks at the header, and decides where to send it based on its
    adjacent switches
- They _do not_ maintain state information about the network
  - It knows nothing about the network as a whole, and only makes decisions
    based on each individual packet
