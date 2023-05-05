---
id: "Transport Layer"
aliases:
  - "Multiplexing and Demultiplexing Inside a Host"
tags:
  - "CS118"
---

- Run in end hosts, offering a logical communication channel between two
  applications
- Multiple transport protocols exist
  - UDP, TCP: Oldest/most frequent
  - RTP: Real-time transport protocol
  - QUIC: New protocol
- The transport layer handles logical communication between _processes_
  - Relies on the network layer to deliver packets
- The network layer delivers packets hop-by-hop, from source to destination

## Multiplexing and Demultiplexing Inside a Host

- Multiplexing at sender
  - Handles data from multiple sockets, adds transport header (later used for
    demultiplexing)
- Demultiplexing at receiver
  - Use header info to deliver received segments to correct socket

## Demultiplexing

- Host receives an IP packet
  - Contains source and destination IP (in the header)
  - Carries a single transport-layer data _segment_
- Host uses the IP addresses and port numbers to direct each segment to the
  right socket (essentially "reassembling" the message)

## What Protocol "Layer" Means

- How much data can each transport segment carry?
  - The limit comes from a lower layer (MTU, Maximum Transmission Unit)
  - TCP chops up a bye stream into segments
  - Apps running over UDP try to make a UDP segment fit into one MTU

## Connectionless (UDP) Demultiplexing

- When sending a packet to a UDP socket, one specifies the destination IP
  address and port number
- Destination host directs incoming packets to the socket listening to the
  destination port number
- Packets with the same address/port number are directed to the same socket
  - Even if they have different sources
  - The source/destination are just swapped for the server, so replies can be
    sent to the correct clients

## Connection-Oriented (TCP) Demultiplexing

- A TCP socket is identified by a 4-tuple:
  - Source IP/port number
  - Destination IP/port number
- Host can use the tuple to direct segments to the right socket
- Many TCP sockets can be supported in parallel
- A web server creates separate sockets for each connected client

## UDP

- Segment may be lost, duplicated, or out of order
- All segments are handled independently of one another
- Usage:
  - DNS
  - Streaming multimedia (loss-tolerant)
- Header
  - Simple, small (2 bytes for source/destination port numbers, length, checksum)
  - No delivery guarantee nor congestion control

## UDP Checksum

- Goal: Detect bit errors in the segment
- Sender: Sum up everything and put the complement in the checksum field
  - Optional for UDP: Set checksum field to all 0's if not used
- Receiver: Add up everything (including the checksum) and see if it is all 1's
- The header should also contain a pseudo-header, which protects against
  misdelivered IP packets
  - The header is not carried in the UDP packet, nor counted in the length
    field, but is used in computation
- Three basic components for reliable delivery via retransmission
  - Sender side:
    - Each piece of data needs a unique ID
      - Discard duplicates based off of the ID
    - Set a retransmission timer after sending a packet
      - If `ACK` received, cancel the timer, otherwise retransmit
  - Receiver side: Send an acknowledgement after receiving the expected data

## Reliable Data Transfer

- Three questions
  - How many different kinds of errors?
  - How to detect each type of error?
  - How to recover from each type of error?
- Three types of errors, and how to detect them
  - Corrupted bits: detected by checksum
  - Packet loss: receiver sends acknowledgement and sender sets an alarm timer
    for receiving the acknowledgement
    - Packets arriving out of order: Assign each packet a sequence number
  - Recovery: Retransmit the bit-error/lost packet

## Design 1: Stop and Wait

- If $B$ receives a packet from $A$ that has a bit error
  - $B$ doesn't send `ACK`
  - $A$ times out and retransmits

## Design 2: Stop and Wait with NACK

- When $B$ receives a packet with an error
  - $B$ sends an `ACK` with the ID of the last correctly received packet
  - A treats the _duplicate_ `ACK` as a negative-ACK, and retransmits the
    corresponding packet
- Problem: Still waiting for most of the time

## Design 3: Pipelining Packet Transmission

- Allow for multiple, to-be-acknowledged packets to be in transit at the same
  time
  - Buffer in-flight packets at the sender: if packets get lost, retransmit
  - Buffer size determines how many packets can be in-flight, also known as the
    _flow control window_
- What if some packets get lost?
  - Go-back-N (GBN)
    - Sender can send up to $N$ unacknowledged packets
    - $N$ is the flow control window size
  - Receiver sends a cumulative acknowledgement, acknowledging only the last
    in-order received packet
  - Sender sets timer for oldest unack'ed packet
    - When the timer expires, retransmit _all_ unack'ed packets
  - When an out-of-order-packet is received, discard and wait for the correct
    one
- Improvements
  - Selective repeat
    - Sender sends up to $N$ unack'ed packets
    - Receiver _individually acknowledges_ correctly received packets
    - Sender maintains timer for each unack'ed packet
      - Retransmit _only that packet_ when timer expires
    - Flow control window works the same
      - Sender dan send $N$ consecutive packets
    - How many bits do we need?
      - If the window size is 4, then 2 bits is _not_ enough because packets can
        get lost
      - The window size must be ≤ (the # of bits + 1) / 2
