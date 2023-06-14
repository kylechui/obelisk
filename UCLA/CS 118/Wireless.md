---
id: "Wireless"
aliases:
  - "Ad Hoc Model for Wireless Networking"
tags:
  - "CS118"
---

- Elements of a wireless network:
  - Wireless links: Connects mobile devices to base station, runs over a
    multiaccess protocol
  - Wireless host: May be stationary or mobile
  - Base station (or Access point): Typically connected to wired network,
    forwards packets between wired network and wireless hosts in its "area"
  - Infrastructure mode:
    - Base stations connect mobile devices to wired networks
    - Mobile devices switch base stations after moving for continued internet
      access (handoff)
  - Ad hoc mode:
    - No base stations
    - Each node helps forward packets to other nodes

## Ad Hoc Model for Wireless Networking

- No base station
- A node transmits to other nodes within its link coverage
- Nodes interconnect into a network, and exchange information about who can
  reach whom
- However, there has been no deployment
  - This is because it is hard to keep track of identification and security
    without pre-configuration

## Problems with Wireless Channels

- Hidden terminal: If two nodes that don't know about each other send to the
  same node at the same time, a collision occurs
- Signal attenuation: Two nodes have weak signals with each other, but strong
  with a third node, causing interference

## IEEE 802.11 LAN Architecture

- Access point (AP), also known as base station
  - Basic service set (BSS): Contains wireless hosts and AP
  - Service set identifier (SSID)
- 802.11 divides the spectrum into channels at different frequencies
  - Administrator chooses frequency for AP
  - If neighbor APs use the same channel, there is interference
- AP sends beacon frame periodically, which contains SSID and its own MAC
  address
- Arriving host: Must associate with an AP before transmitting
  - Scan channels, listening for beacon frames
  - Select an AP to associate with by initiating the association protocol
  - Run DHCP to get IP address in AP's subnet

## IEEE 802.11 Multiple Access

- Like Ethernet, it uses CSMA: Sense the channel before transmitting
- We should allow the sender to "reserve" a channel, to avoid collisions when
  transmitting long data frames
  - Sender first sends a request-to-send (RTS) packet using CSMA
  - AP broadcasts clear-to-send (CTS) in response, if there is no collision
  - CTS is heard by all nodes in the AP's wireless range, and other stations
    defer transmission until the sender is done

## 802.11: Mobility Within a Subnet

- $H_1$ remains in the same IP subnet: IP address can remain the same
- $H_1$ detects a weakening signal from $AP_1$, so it scans and finds $AP_2$ to
  attach to
- Switch's perspective: Which AP is associated with $H_1$?
  - Self-learning: It will see frames from $H_1$ and "remember" which switch
    port can be used to reach $H_1$

## Spectrum of Mobility Support

- Network must answer two questions:
  - If a host moves, does its IP address change?
  - Must the communication continue while a host's IP address change?
    - If so, a method to make this transparent is necessary

## IP Mobility: Basic Concept

- Every host has a home
  - Stationary host: always home
  - Mobile host: may move away from home
- When a mobile host is not home, it gets a foreign address (care-of-address)
  - Notifies home of its new address

## IP Mobility: Vocabulary

- Home network: Permanent home of mobile device
- Home agent: Entity that performs mobility functions on behalf of mobile host
  when mobile is away from home
- Permanent address: Mobile's address in home network
- Correspondent: Computer that wants to communicate with mobile
- Visited network: The network where mobile host currently resides
- Care-of-address: Address obtained from the visited network

## Mobile IP: Tunneling

- Home agent tunnels the message to the mobile host
- Mobile could use its home address
  - But could be dropped if the network verifies the source address
- Or mobile could tunnel a packet to the correspondent

## Mobility Summary

- Mobile uses two addresses: permanent and care-of-address
- Mobility is transparent to the correspondent
- It may result in triangle routing, where the correspondent sends to the home
  network, which tunnels to the mobile host
  - This adds overhead and can make things very slow if the home agent is very
    far

## Mobility via Direct Routing:

- Correspondent requests care-of-address of mobile, then directly communicates
  with mobile
- This eliminates transparency for the correspondent
- Also the case when the mobile moves again needs to be handled
