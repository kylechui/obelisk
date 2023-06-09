---
id: "Network Layer"
aliases:
  - "Network Layer"
tags:
  - "CS118"
---

## Network Layer

- The protocol exists in _every_ host and router
- The source host encapsulates data segments from the transport layer into _IP
  packets_
- The destination host removes the IP header, and delivers the segments to the
  transport layer
- Each router along the path moves packets towards the receiving host
  - Routing: Fill in the router's forwarding table with the best path to each
    destination
  - Forwarding: Use the destination address in each packet to find the next hop
    along the best path

## The Internet: A Datagram Network

- Hosts are connected to subnets
- Different subnets are interconnected by routers
- All hosts and routers are able to use IP
- IP provides two basic functions
  - Datagram delivery (best-effort) from source to destination hosts
  - Fragment packets along the way if needed (reassemble at the destination host
    before passing along to transport layer)

## IP Datagram Format

- The minimum byte size is 20 bytes
- The data is of variable length, but is usually the size of a TCP or UDP
  segment

## IP Fragmentation and Reassembly

- Different subnets have different maximum transmission unit (MTU)
- Sending host uses its local MTU size
- If the next link has a smaller MTU, the router fragments the IP packets
  - Cut up the packets into sizes of the next link's MTU
  - Further fragmentation could happen
- Fragments get reassembled at the destination host
  - They are not reassembled at each router, in case the fragmentation happens
    again, further down the line
  - Receiving host sets a timer after getting the first segment (not necessarily
    in-order) of an IP packet
    - If a full packet is received, assemble it and send it to the transport
      layer
    - If timeout, then delete received segments

## IPv4 Fragmentation Details

- Identifier: generated by the sending host
  - It identifies all segments from the same packet
  - It should stay unchanged when re-fragmented
- Flags
  - Bit 0: Reserved (left most bit)
  - Bit 1: Don't fragment
  - Bit 2: More fragments
    - MF is set to 0 in the last segment
- Fragment offset: Used to reorder the segments upon arrival
  - Counts from the first byte in the original payload
  - Counts in units of 8-byte blocks
- Total length and header checksum is adjusted when the packet is fragmented
- The header length field tells you the length of the header (in units of 4
  bytes), e.g. length 5 → 20 bytes
- The data field length must be a multiple of 8 bytes, except possibly the last
  one

## What an IP Address Identifies

- IP assigns a globally unique IP address to each _attachment point_
  - For example, a laptop can have multiple IP addresses for different
    interfaces (i.e. Ethernet, WiFi)
    - This is particularly true for routers

## IPv4 Address Structure

- It is 32 bits, uniquely identifying a host or router _interface_
  - Interface: Connecting point between host/router and physical link
- How do we define IP ranges in routing table?
  - They should be compact
  - They should be fast and easy to process
  - We designate a number of bits for the "Network ID", and the routing table
    will contain only network IDs

## How Many Bits For Network ID?

- Originally (RFC791), we used class-based address
  - There were a number of bits that determined the size of the host address
- It is no longer in use

## Today's IPv4 Address Structure

- We needed further substructure in the IP addresses
- Two changes were added:
  - Subnetting: An organization gets one address block, then splits it into two
    parts (subnet and host)
  - CIDR (Classless InterDomain Routing): The network portion can take an
    arbitrary number of bits

## IP Subnet

- Subnet mask: Indicates the portion of the address is considered as the
  "network ID" by the local site
  - It doesn't need to be byte-aligned
- Backbone routers only know how to forward packets to the network ID
  - Within the network identified by network ID:
    - Routers store: {subnet, mask, next hop}
    - Every host is configured with its IP address and associated subnet mask

## CIDR Address Format

- `a.b.c.d/x`
  - `a.b.c.d`: Network address
  - `x`: Number of bits in network ID portion of the address
  - `1100100 00010111 0001000 00000000` is `200.23.16.0/23`, where the first 23
    bits form the network ID
- Network mask format
  - `a.b.c.d`, with network mask `e.f.g.h`
    - `a.b.c.d`: Network address
    - `e.f.g.h`: Network ID portion is all 1s and host part is all 0s
    - Address `200.23.16.0`, with netmask `255.255.254.0`

## Hierarchical Addressing: Route Aggregation

- Hierarchical addressing allows for route aggregation, which reduces global
  routing table size
  - Like splitting the IP address into chunks, where each chunk is handled by a
    different router

## IP Packet Forwarding: Longest Match Lookup

- Destination-based forwarding: Only look at destination addresses
- Routing protocol builds forwarding table (FIB) in all routers
  - The FIB maps each IP prefix to an outgoing interface
- To forward a packet, the router finds the longest-matching prefix entry for
  the destination address

## Summary

- Both CIDR and subnetting are ways to utilize the IP address space
