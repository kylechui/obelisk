---
id: "Link Layer"
aliases:
  - "Data Link Layer"
tags:
  - "CS118"
---

## Data Link Layer

- Link layer transfers from one node to a physically connected node
  - Where nodes are routers or hosts
- Implementation of link layer technologies
  - Ethernet, wireless LANs, LoRA, etc.
- They encapsulate IP packets in another header (in addition to network,
  transport layers)

## Link Layer: Basic Concepts

- Link layer address: MAC (Medium Access Control) address
  - Should be globally unique
- Link type: Simplex, half-duplex(multi access links: Ethernet, WiFi), full-duplex
- Link layer functions:
  - Data framing (marking the start/end of a chunk)
  - Error detection
  - Channel access protocols

## Data Framing

- For a block of data (that has different names at different layers):
  - At link layer: A data frame
  - At network layer: A packet
  - At transport layer: TCP (segment); UDP (datagram)
    - A segment is a piece of the whole message, while a datagram is standalone
- A frame has a header field
  - And optionally a _trailer_ field
- Each IP packet gets put into one frame, since they are datagrams
- Byte-oriented framing protocol: Delineate the frame with a byte of a special
  bit sequence `0b01111110` _before the link layer header_ (for physical layer
  reasons)
  - If the bit sequence appears in the data, we perform byte stuffing

## Byte Stuffing

- After each `0b01111110`, we "stuff" an extra byte of `0b01111110`
  - If we see a single byte, then it's a flag
  - Otherwise, we treat it as a raw byte
  - This is basically the same as using `\` to "escape" characters

## Multiple-Access Links and Protocols

- Sharing a single transmission medium can lead to collisions
  - If multiple parties use the bandwidth at the same time
  - Then receivers cannot decode frames
- Multi-access protocols "coordinate" when nodes can utilize the bandwidth
  - "Hard" coordination
    - Collision avoidance, at the cost of
  - "Soft" coordination
    - Most modern protocols implement this

## Multiple Access Control

- Ideally, $M$ nodes would share a bandwidth of $R$ by each using $\frac{R}{M}$
  resources
  - We also wish for the protocol to be simpler, with no central controller
    - No special node to coordinate transmission
    - No synchronization of clocks or slots
- There are three classes of solutions:
  - Channel partitioning: Divide the channel into pieces by time, frequency,
    code, etc.
  - Taking turns: Coordinated access to avoid collision
  - Random access: There is no coordination, just avoid collisions if possible
    (and resolve them when they do occur)

## "Taking Turns" MAC Protocols

- _On-demand_ channel allocation
- Polling:
  - Main node needs to ask other nodes to transmit in turn
  - Concerns:
    - Polling overhead
    - Latency
    - Single point of failure (the main node)
- Token passing:
  - One token message is passed from one node to the next (sequentially)
  - Whoever gets the token sends a data frame, then passes the token to the next
    node
  - Similar to the "speaking baton" (or other item)
  - Concerns:
    - Latency
    - Single point of failure (the token)
  - A main station generates the token and monitors its circulation
    - If the token disappears or is lost, generate a new one

## Random Access Protocols

- Let a node transmit at a full channel rate $R$
  - There is no a priori coordination among nodes
  - If a collision occurs, detect it and recover
- When a collision occurs, a random access protocol figures out
  - How to detect it
  - How to recover from it
- Examples: ALOHA, slotted ALOHA, CSMA/CD, CSMA/CA

## ALOHA History

- Developed in Hawaii, as the first wireless packet-switched network
- Why ALOHA
  - Mountainous islands rendered a wire-based network infeasible
  - Radio channels had high error rate, so centralized control was infeasible
- Upload channel: Contention-based random access
- Download channel: Rebroadcasting all received packets

## ALOHA

- If a node has data to send, send the whole frame immediately
  - If there is a collision, retransmit with probability $p$
  - First come, first serve
- Collision probability:
  - Assuming all frames are of the same size, then a frame sent at $t_0$ may
    collide with frames sent in $[t_0 - 1, t_0 + 1]$
- Efficiency:
  - Probability $p$ to transmit one frame by one node in $[t_0, t_0 + 1]$, but:
    - No other node can transmit during $[t_0 - 1, t_0]$
    - Or during $[t_0, t_0 + 1]$
  - We compute it to be
    $$
    \begin{align*}
      p\cdot p_1\cdot p_2 &= p\cdot (1 - p)^{N - 1}\cdot (1 - p)^{N - 1} \\
                          &= p\cdot (1 - p)^{2(N - 1)}
    \end{align*}
    $$
  - Thus the optimal choice of $p$ as $N\to\infty$ yields an efficiency of
    $\frac{1}{2e} = 0.18$

## Slotted Aloha

- Assumption:
  - Time is divided into equal time slots
  - Clocks are synchronized
  - All nodes can detect a collision
- Nodes only transmit at the beginning of the next slot
  - If no collision, a node can send a new frame
  - Otherwise, retransmit with probability $p$ in subsequent slots

## Efficiency of Slotted ALOHA

- We compute the efficiency to be $p\cdot (1 - p)^{N - 1} = \frac{1}{e} = 0.37$

## CSMA: Carrier Sense Multiple Access

- Key Idea: Listen to the channel before transmitting
- If the channel is idle, then transmit
- Otherwise, wait until it's idle before transmitting
  - 1-persistent CSMA: Retry immediately
  - $p$-persistent CSMA: Retry immediately with probability $p$
  - Non-persistent CSMA: Retry after a random interval
- Collisions are still possible, and it goes up with the distance between nodes
- To cut the loss early, do CSMA/CD

## CSMA/CD: Carrier Sense Multiple Access/Collision Detection

- Collision detection: Compare the transmitted and received signals
- Abort collided transmissions

## Ethernet CSMA/CD Algorithm

- NIC receives datagram from network layer, and creates the frame
- If the channel is idle, start the frame transmission
  - Otherwise, wait until it is idle and transmit (1-persistent)
- If NIC transmits the entire frame without detecting another transmission, you
  are done!
- If NIC detects another transmission while transmitting, it aborts and sends a
  jam signal for a short time period
- After aborting, NIC enters binary exponential backoff:
  - After the $m$th collision, NIC chooses a value $K\in \left\{0,
    1,\dotsc,2^m - 1\right\}$
  - It then waits for $K$ slots, and queries the channel for idleness
    - Each slot is the transmission time for 512 bits
  - With more collisions, the backoff interval is longer

## CSMA/CD Efficiency

- $T_{\mathrm{prop}}$ is the maximum propagation delay between any two nodes
- $T_{\mathrm{trans}}$ is the time to transmit a maximum-sized frame
- Then the efficiency is given by
  $$
  \mathrm{efficiency} = \frac{1}{1 + 5T_{\mathrm{prop} / T_{\mathrm{trans}}}}
  $$
- As $T_{\mathrm{prop}}$ goes to 0, efficiency approaches 1
- As $T_{\mathrm{trans}}$ goes to $\infty$, efficiency approaches 1
- Note that as speed goes up, transmission delay goes down, so efficiency is
  going down as well

## Ethernet

- Ethernet was the dominant LAN technology until WiFi
- It kept up with the speed race from 10Mbps to 100Gbps
- Bus topology popular through the mid 90s
- As speed went up over time, we moved to switch-based star topology

## Ethernet Frame Structure

- Sending adapter encapsulates IP datagram in Ethernet frame
- Preamble (8 bytes): 7 bytes `0b10101010` followed by `0b10101011`, used to
  synchronize clock rates

## MAC Addresses

- Ethernet and WiFi use 48-bit MAC addresses
- They are hard-coded into the adapter (with exceptions)
  - IEEE controls MAC address allocation
- Manufacturers by MAC address blocks from IEEE
  - Guarantees uniqueness
- MAC address is flat, so it is portable
- IP address is hierarchical, so it isn't portable
