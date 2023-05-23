---
id: "Routing Algorithms"
aliases:
  - "Tunneling"
tags:
  - "CS118"
---

- Transition from IPv4 to IPv6 cannot happen instantaneously
- The internet must be able to operate with mixed routers
- One proposed solution was to use a dual stack
  - However, this doesn't solve the issue of running out of IPv4 addresses

## Tunneling

- Most of the internet still runs on IPv4
- Currently, we have IPv6 packets tunneling through an IPv4 network
  - IPv6 packet inside a IPv4 packet

## Network-Layer Functions

- Forwarding: Move packets from router's input to appropriate output interface
  (data plane)
- Routing: Determine the path taken by packets to reach destinations
  (routing/control plane)
- Two ways to structure network routing/control:
  - Per-router control (traditional)
    - Each router runs routing protocol to set up forwarding table
  - Logically centralized control (recent)
    - SDN: Software-defined networking

## Per-router Control Plane

- Each router runs the _routing algorithm_ to compute forwarding table, using
  the information learned from other routers via _routing protocols_
- We use algorithms like Dijkstra's or Bellman-Ford in order to compute the
  shortest path
- The routing protocols define the format of how information is exchanged
  between routers
  - Network topology changes, so the routing protocol informs all routers of the
    latest changes

## Link-state Algorithm (Dijkstra)

- Every node knows the network topology graph with link cost
- Each node computes least cost paths from itself to all other nodes
- After $k$ iterations, a node knows the best paths to $k$ destinations
- Notation:
  - $c(x, y)$: Link cost between nodes $x, y$
  - $D(v)$: Current value of cost path from source to destination $v$
    - Gets initialized to $\infty$
  - $p(v)$: The node right before $v$ along the best path from source to $v$
- This runs in $O(n^2)$ time, and there exists a faster $O(n\log n)$ algorithm

## Distance Vector Algorithm

- Each node computes shortest path based on the input from all neighbors
- Each node sends its distance vector (list of distances to neighbors) to all of
  its neighbors, and receives distance vectors from each of its neighbors
