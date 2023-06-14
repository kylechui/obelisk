---
id: "Routing Protocols"
aliases:
  - "BGP: Border Gateway Protocol"
tags:
  - "CS118"
---

## BGP: Border Gateway Protocol

- BGP provides each as a means to:
  - Advertise its own prefixes to the rest of the internet
  - Obtain IP address prefixes reachability information from neighboring
    autonomous systems
  - Propagate the reachability info to all routers _internal_ to the autonomous
    system
  - Determine the "good" routes to use for learned reachability to destination
    prefix and policy
- Distributing path information
  - Two neighbor BGP routers establish a BGP session over TCP, exchanging
    routing info
    - Advertising routes to destination network prefixes
  - When a router advertises some prefix, it guarantees that it will forward
    packets towards that prefix
- Path attributes and routing policies
  - BGP update: A prefix + attributes is a "route"
  - Import policy: Which paths should the router keep/drop?
  - Route selection: Among multiple routes for a destination, which one should
    be used?
  - Export policy: Which neighbors should know about which destinations?
- There are three important attributes:
  - AS-PATH: A list of autonomous systems through which prefix advertisement has
    passed
  - NEXT-HOP: Indicates specific internal-AS router to next-hop AS
  - Local preference: Indicates policy preference in path selection
- BGP has no built-in routing metric
  - It may select the "best" route via: local preference, shortest AS path,
    closest NEXT-HOP router

## Internet AS Interconnects

- Tier-1 ISPs are fully connected with one another, without any providers
- Regional ISPs
  - Customers of tier-1 ISPs
  - Can peer with other regional ISPs
- Customer stub networks
  - Multihomed in general
    - Means that it is connected to multiple provider networks
  - Special case: Super-giants
- Customers do not reveal any route information to its providers, since they do
  not want to forward traffic between providers
  - They are basically terminal nodes, and don't propagate information any
    further
- For peer-to-peer connections, providers only tell other peers about the
  reachability of their customers
- When a provider owns an IP address, it is treated as its own customer (I
  think)
- Why different Intra vs. Inter AS routing?
  - Policy:
    - Inter-AS: Admin wants control over how the traffic is routed, i.e. who is
      routing through the network
    - Intra-AS: Single admin, so no policy is needed
  - Scale: Hierarchical routing saves table size
  - Performance: Intra-AS focuses on performance, Inter-AS focuses on policy
