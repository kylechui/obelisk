---
id: "LANs and Switches"
aliases:
  - "ARP: Address Resolution Protocol"
tags:
  - "CS118"
---

## ARP: Address Resolution Protocol

- Every IP node (host & router) runs ARP to build an ARP table
- Each table entry consists of IP address, MAC address, and TTL
  - When an entry is looked up, the TTL value gets reset
- Soft-state design: Information deletes itself after a certain time _unless it
  is being refreshed_
- Nodes are able to create their ARP tables without administrator intervention

## Example: Sending an ARP Request

- Suppose $A$ wishes to send a datagram to $B$
  - And B's MAC address is not in $A$'s ARP table
- $A$ broadcasts an ARP query that contains $B$'s IP address
  - The destination MAC address is `0xFFFFFFFFFFFF` (broadcast)
  - All nodes on the local access network receive the query
- $B$ receives the query
  - It adds $A$'s information to its ARP table
  - The reply frame contains its own MAC as the source, and $A$'s MAC as the
    destination
- $A$ receives the response
  - $A$ adds $B$'s entry into its ARP table
- After the exchange, both $A$ and $B$ have learned of each other's MAC
  addresses

## Ethernet Frame Length Limit

- All packets/frames have an upper bound on length
- Ethernet has a lower bound for reliable collision detection
- A transceiver can send and listen at the same
  - If the received data stream differs from the one transmitted, there has been
    a collision
    - To detect the collision, the sender must be transmitting when the garbled
      signal propagates back

## Ethernet: From Shared Cable to Switches

- As speed goes up, the efficiency goes down
- An Ethernet switch is a link layer device that behaves like a host on a
  connected LAN
  - It provides transparency, since the hosts are unaware of the presence of
    switches
  - Store-and-forward: Examine each incoming frame's MAC address, and forward to
    the destination LAN if it's on a different LAN
- Each switch has a forwarding table, with
  - The MAC address of the host
  - The interface to reach that MAC address
  - The TTL

## Building a Forwarding Table By Self-Learning

- When the switch receives a data frame, look at the _source_ MAC address
- If the address is not yet in the table, record it
  - Each entry contains the MAC address, interface, and TTL
  - When the timer expires, the entry gets dropped (TTL can be 60 mins)
- Use the table to look up MAC destination address
  - If a matching entry is found:
    - Reset the TTL
    - If the destination is on the interface where the frame came from then drop
      it, otherwise forward it
  - Otherwise forward to all other interfaces (except the arriving interface)
    - AKA flood
- Switches can also be interconnected, but rely on the assumption that the
  network graph is a tree

## Host Configuration

- An IP host must be configured with the following to send and receive data:
  - IP address of an interface
  - Subnet mask
  - Default router's IP address
  - DNS caching resolver IP address(es)
- This can be hard-coded by a system administrator in a configuration file
- It can be obtained by running DHCP

## Connecting Link and IP Layers

- When node $A$ sends an IP packet to $B$:
  - $A$ looks up the IP address of $B$, and finds out whether or not they are on
    the same subnet
    - The same subnet mask is then applied to both source and destination IP
      addresses
    - If they have the same subnet ID, then they are in the same subnet
      - Otherwise, they have to communicate via the router
- $A$ sends packets to $B$ using a link layer protocol
  - By putting the IP packet inside a link layer frame
- When the router or node receives the frame, the Ethernet header is removed,
  and the IP destination address is read
  - If the destination IP address is "self", it's delivered to transport, which
    then delivers to the application
  - Otherwise, repeat the previous steps
    - Lookup routing table, lookup ARP, etc.

## Switches vs. Routers

- Both are store-and-forward devices
  - Routers: Network layer services (looking at IP headers)
  - Switches: Link layer services (looking at Ethernet headers)
- Building forwarding table
  - Routers run routing protocols, and switches implement self-learning
    algorithms

## Switches: Advantages and Drawbacks

- Transparent: No changes to hosts
- Isolates collision domains, increasing total maximum throughput
- Can connect Ethernets of different speeds, because it is store-and-forward
- Constrained topology: Tree structure only
  - All inter-segment traffic is concentrated on a single tree
  - All multicast traffic forwarded to all LANs

## Routers: Advantages and Drawbacks

- Supports arbitrary topologies
- Requires IP address configuration
- More complex packet processing than switches
- Switches do well in smaller settings, while routers are used in larger
  networks
