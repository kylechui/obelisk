---
id: "Domain Name System"
aliases:
  - "Hierarchical Name Space"
tags:
  - "CS118"
---

- Applications use website names (i.e. URL), and the IP needs the address to
  deliver packets
  - The DNS translates between names and IP addresses
  - Your browser queries the DNS with some name, and the DNS responds with the
    IP address
- This is run over [[UDP|UDP]] by default (which is unreliable)
  - It can also be run over [[TCP|TCP]]
- A domain name is the sequence of labels from a node to the root, separated by
  dots, left to right
  - It identifies its position in some name space
- The DNS is comprised of four main parts:
  - A hierarchically structured name space
  - A distrusted database, maintained by a hierarchy of authoritative servers
    - Designed to be resilient to single points of failure
  - Local DNS servers (caching resolvers)
    - Each host runs a resolver routine (stub resolver) which talks to the
      caching resolver provided by the host's ISP
    - Designed to have caching
  - DNS query protocol used by local caching resolvers to query authoritative
    servers
    - Also used for stub to caching resolver communication

## Hierarchical Name Space

- The depth of the tree is variable
- Each leaf node is a DNS name, and each non-leaf node is a domain
  - Domains belong to administrative authorities
  - Delegated domain can set up sub-domains, with a tree depth limit of 127
- Names are independent of location in the tree
- ICANN oversees assignment of top level domains (TLDs), delegation of TLD
  managements, and operation of root name servers
  - Root authoritative nameservers contain names/IP addresses for all TLDs, and
    are a result of volunteer efforts
- TLD operators run TLD name servers, and allocate 2nd level domain names, i.e.
  `edu` allocates `ucla.edu` to UCLA
  - Each level assigns names to the next level
- The maximum length of a DNS name is 255 bytes

## Authoritative DNS Servers

- Provided/owned by the _owner_ of each DNS name domain $D$
- Serves queries for the names in $D$
- Each domain owner _must provide_ multiple authoritative name servers
  - The main server contains the main file
    - Contains all the data records in the domain
      - Name to address mapping records
      - The DNS server information of child domains
  - The secondary servers contain replicated copies of the main file
    - The main server establishes what "truth" is; the other servers are there
      for performance reasons
- All data is stored in a "[[Resource Record|resource record]]" (RR)
  - It contains four fields: name, type, time-to-live (amount of time a packet
    is set to live before the router clears it), value

## Root Authoritative Nameservers

- The main file of the root domain, containing the names and IP addresses of the
  authoritative DNS servers for _all_ top-level domains (TLDs)
- The root domain file is published on 13 authoritative root servers, named 'a'
  through 'm'

## TLD Authoritative Nameservers

- ccTLD: Provided by each country's government
- gTLD: ICANN delegates management to specific organizations
  - Verisign is in charge of `.com`
  - EDUCAUSE is in charge of `.edu`
    - UCLA is in charge of `ucla.edu`

## Local DNS Servers

- Also known as _caching resolvers_
- They query authoritative servers for users, and cache the data from replies
- Stub resolvers (user-side) send DNS queries to caching resolvers
  - Your computer gets configured with the IP address of caching resolvers
  - When an app needs to communicate over the network, it first uses DNS to
    translate the name to an IP address, before opening a socket with that
    address
    - Syscall: `getaddrinfo()`

## Bootstrapping DNS Resolution

- Stub resolvers
  - Needs to know the IP address for at least one caching resolver
    - Otherwise the query will never make it to an authoritative server
  - Configured with the IP address
    - Manually or via dynamic host configuration protocol (DHCP)
- The caching resolver needs to know the IP address of root servers, which is
  public knowledge

## Summary

- A user queries their local DNS caching resolver
  - Provided by the ISP (or Google/CloudFlare)
- The caching resolver:
  - Finds the answer in cache and return it, or
  - Queries one of the root servers
- The root servers reply to the caching resolver with the right IP address if
  they have it, or point to another root server that is "closer"
  - Eventually the caching resolver gets the IP address, and then forwards it to
    the user

## Query Handling

- Recursive: The server takes responsibility of finding the final answer, and
  sends it back to the caching resolver
  - The server has to do a lot of work
  - The caching resolver has an easy job and just waits to be spoon-fed the
    answer from the authoritative nameserver
- Iterative: The server sends an answer back to the resolver directly
  - Either returns the matching reply, or a referral to another server
  - Servers can fill in their caches more effectively
  - Resolvers have to do a lot more work

## Scaling DNS Services By Caching

- Caching resolver saves a copy of all the query replies
  - Popular sites tend to be found in the cache
- Stale entries should be removed from the cache
  - This is done by attaching a TTL value (set by the DNS data owner) to each
    DNS reply
- A low TTL is desirable because it minimizes periods of inconsistency, while a
  high TTL minimizes traffic

## Providing Robust DNS Service

- Robust: High availability against network or server failures
- Two basic ways to achieve this: redundancy and caching
  - Redundancy: replicating authoritative servers
  - Caching: creating redundant data copies
- Caching resolvers save a copy of all query replies
  - Authoritative servers attach a TTL value to each reply, after which the
    cache entry is deleted
  - Caching resolvers typically have information about top-level domains, so
    they don't visit the root server very often

## DNS Is Not An Automated System

- DNS defines:
  - Standard formats for formatting/storing DNS data (resource records)
  - Standard methods for querying the database (the DNS protocol)
  - Tuning knobs of DNS server configurations, caching period, etc.
- Operators:
  - Define zone boundaries and subzone delegations
  - Define desired refresh policies
    - Caching (TTL)
    - Main -> secondary synchronization
  - Manually update the main files
    - Contact the parent zone's operator for nameserver updates
    - More recently: dynamic DNS

## Why is DNS Decentralized?

- No single point of failure
- Able to handle more traffic volume
- Easier to keep all resource records updated
- Shortens distances between database servers and clients

## Anycast Forwarding

- Unicast: A given IP address block $A$ is announced from a single location
- Broadcast: Send packets with IP broadcast address as destination everywhere
- Multicast: An IP multicast address represents a group of recipients
  - Needs fundamental changes to IP forwarding
  - Needs routing protocol support
- Anycast: A given IP address block $A$ is announced from multiple locations
  - A route receives reachability to $A$ from multiple neighbors; pick the
    shortest path to forward packets

## A Few Comments

- Stub resolver keeps a local cache
- The stub resolver can send queries to authoritative servers directly, but it
  is slow
- Caching resolvers: A service process
  - Listen to (TCP or UDP) port 53, waiting stub resolver requests
- When I get a name $N$, can I allocate more names under $N$?
  - It depends on whether the parent domain allocated or delegated $N$ to you
  - Once delegated, the parent domain can't control how a child domain manages its
    namespace

## Using DNS for Content Distribution Networks

- Caches can be provided by content owners
  - CDN providers offer a caching service
  - Content owners pay for the service

## How to Get HTTP Requests to Nearby CDN Server

- A user queries DNS to get some website (say `cnn.com`), and sets up a TCP
  connection
  - The DNS server should return the IP address of the nearest CDN server
- `cnn.com` pays for CDN service, outsourcing `cnn`'s DNS service to the CDN
  provider
  - When the DNS server receives a query, the source IP address is received from
    the query
  - The address is used to approximate the user location, and then a nearby CDN
    box is returned
- If the website turns on HTTPs, the crypto key is shared with the DNS server,
  and the browser believes it's connected to `cnn.com` directly

## Attacks

- Brute force DDoS attacks
  - Bombard root servers with queries (usually doesn't work)
  - Bombard lower-level servers, that have fewer resources
- Man-in-the-middle attacks
  - Intercept queries and send bogus replies to caching resolvers
  - Also known as _cache poisoning_
    - There is no way to determine the validity of the information just by
      looking at it

## Abusing DNS as an Attack Tool

- Send queries with a _spoofed_ address (the victim's IP address)
- Use a large number of compromised devices to amplify the attack
  - All of the DNS servers then send information to the victim
- One way to mitigate this is to use DNS over TCP instead of UDP
