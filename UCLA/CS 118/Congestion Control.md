---
id: "Congestion Control"
aliases:
  - "How Network Congestion Happens"
tags: []
---

## How Network Congestion Happens

- Too many sources sending too much data into the network at the same time
- Scenario 1: 2 senders, 2 receivers, one router with an infinite buffer
  - When congested, the throughput reaches a maximum and the delay goes to
    infinity
- Scenario 2: One router, finite buffer
  - Senders will retransmit when timing out
  - Packets may get dropped if the buffer is full
  - Known loss: Sender only retransmits if a packet is known to be lost
  - Duplicates: Sender may time out prematurely and retransmit, so some
    duplicates will be delivered
- Scenario 3: Circular dependencies

## TCP Congestion Control

- Window-based flow control (cwnd)
- Send out the minimum of the cwnd and rwnd
- We adjust the cwnd size based on network traffic, i.e. congestion is inferred
  via packet losses

## Window Adjustment

- Two phases:
  - Slow start: Set CC window size to 1 segment (start slow, but _rapidly_
    increase)
  - Congestion avoidance: Slowly but continuously increase the CC window size
- Use the slow-start threshold (`ssthresh`) to define the boundary between the
  phases
  - If the window is smaller than the threshold, grow faster
  - If the window is larger, increase cwnd by one segment per RTT

## Slow Start

- Goal: Find the pipeline size quickly
- Set cwnd = 1 MSS (max segment size)
- Send the segments
  - For each ACK received, cwnd += 1 segment
  - If we timeout, ssthresh = cwnd / 2, reset cwnd = 1 MSS, resend segments

## Congestion Avoidance

- Additive increase, multiplicative decrease (AIMD)
- Cautiously probe for unused resources, and quickly recover from overshooting
- Send cwnd segments
  - If all segments are ACKed, then increase cwnd by 1 segment
  - Otherwise cut cwnd in half
- For every ACK received
  - `cwnd(i) = cwnd(i - 1) + (bytes in 1 packet) / cwnd(i - 1)`
- If three duplicate packets are lost
  - `cwnd(i) = ssthresh = cwnd(i - 1) / 2`
- This results in fair sharing of resources over time between multiple
  connections on one network

## TCP Throughput

-
