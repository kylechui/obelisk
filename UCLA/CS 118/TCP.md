---
id: "TCP"
aliases:
  - "Overview"
tags:
  - "CS118"
---

- TCP is a connection-oriented service; it first establishes a connection via
  handshake before sending data
- It is a very simple protocol that provides:
  - Reliable transport
  - Flow control: Making sure neither side of a connection overwhelms the other
    side with too many packets
  - Congestion control: Helps prevent the system from entering gridlock; if the
    router becomes congested then end systems diminish the rate at which they
    send packets into the network
- The application using TCP doesn't need to know about _how_ TCP is implemented,
  just that it does implement the above

## Overview

- Point-to-point: creates a virtual pipe between two processes
- Connection-oriented: sets up a connection first before transmitting any data
- Bi-directional, reliable stream delivery: no "message" boundaries
- Flow controlled: prevents the sender from overwhelming the receiver
- Congestion controlled: mitigates traffic overload inside the network

## Segment Format

- It contains both the source and destination port numbers, since it is
  bi-directional
- There are extra bits in an "optional" field that lets you put more information
  (for future-proofing reasons)
  - For example, metadata related to selective repeating is put in the optional
    field
- If only part of the data has been transmitted and there is a reset, then all
  of the old data gets discarded
- The checksum is computed over the TCP segment _and_ the pseudo header
- The ACK flag contains a sequence number
  - The sequence number of the next byte expected from the other end
- Both the sequence number and receiver window size are also included
  - The sequence number of the first byte in this segment's data

## Connection Management

- Set up the connection before the data transmission starts
  - Each of the two ends reliably informs the other of its initial data byte
    sequence number value
- Close the connection when done
  - Each endpoint informs the other of its final data byte sequence number value
- Abort the connection when any errors occur

## Connection Setup

- Client sends SYN to the server
  - SYN flag is set to 1
  - The client's initial sequence number is initialized to a random value
  - _No data is transmitted_
- Server receives the SYN, and replies with SYN_ACK
  - SYN and ACK flags are both set to 1
    - ACK received sequence number
  - Specifies its own initial sequence number (also randomly)
  - Connection is established client-side
- Client sends SYN_ACK
  - ACK flag is set to 1, signifying that ACK received sequence number
  - May carry data
  - Connection is established server-side

## Example

- (SYN, ACK) pairs between client and server
- Client, server, client
  - (10001, 0) -> (30010, 10002) -> (10002, 30011)
  - The SYN number of the client is the ACK number of the server, and vice versa
  - SYN' = ACK, ACK' = SYN + 1

## Closing

- Client sends a FIN message, setting the FIN flag to 1 (_with no data_)
- The server receives the FIN, and replies with FIN_ACK
  - It's a regular ACK, acknowledging the client's FIN
- When the server finishes its jobs, it sends a FIN
- The client sends FIN_ACK
- The server receives FIN_ACK, closing the connection
- The client waits for some period of time, before timing out and closing the
  connection
  - We wait for twice the longest segment lifetime (TCP's longest segment
    lifetime is 2 minutes)
  - _If we don't properly close the connection, then we lose all of our data!_

## Flow Control

- Receiver informs the sender of the amount of free buffer space
  - Carried in the `RcvWindow`field of the TCP header, so it can change
    dynamically
- Sender keeps the amount of transmitted, unacknowledged data to be no more
  than the most recently received `RcvWindow` value

## TCP Loss Detection and Recovery

- A retransmission timer (RTO) is set to detect packet losses
- The TCP connection sets one RTO on the earliest sent, but unacknowledged
  segment $S$
  - If $S$ gets acknowledged, restart the timer on the next unacknowledged
    segment
- When the timer expires, retransmit starting with $S$
- How many segments to retransmit?
  - Receiver flow control window remaining space `rwnd`
  - Congestion control window remaining space `cwnd`
  - The number of segments that can be retransmitted is the minimum of these two
    values

## Setting the RTO

- The RTO is set based on the estimated RTT and a "safety margin" (DevRTT)
- SRTT: Estimated "smoothed" RTT
  - $SRTT = (1 - \alpha)\cdot SRTT + \alpha\cdot SampleRTT$
  - For the first measurement, $SRTT = SampleRTT$
- DevRTT: Estimated RTT deviation
  - $DevRTT = (1 - \beta)\cdot DevRTT + \beta\cdot \left\lvert SRTT - SampleRTT\right\rvert$
  - For the first measurement, $DevRTT = \frac{SRTT}{2}$
- RTO: Retransmission timeout
  - $RTO = SRTT + 4\cdot DevRTT$
- Typically, we use values of $\alpha = \frac{1}{8}, \beta = \frac{1}{4}$

## One More Question

- How do we set the RTO value for the first segment?
  - If it's too small, we transmit unnecessarily
  - If it's too large, we wait longer than necessary to retransmit

## What to Do in Cases of Retransmissions

- Taking measurement seems infeasible
  - We don't know if we are taking the delay between first transmission and
    final ACK, or final transmission and first ACK
- In case of segment retransmission:
  - Don't take the RTT sample
  - Double the retransmission timeout value (RTO) after each timeout
  - Take the measure again upon the next successful data transmission

## TCP Fast Retransmit

- RTO is set to a long value
  - Minimize extra retransmissions by delaying for longer before resending lost
    packets
- Can detect lost segments via duplicate ACKs
  - When a segment arrives out of order, the receiver sends an ACK for the byte
    it is expecting
- If the sender receives three duplicate ACKs for the same sequence number, it
  assumes the segment was lost
- Fast retransmit: Start retransmitting without waiting for the timer to expire

## TCP Receiver: When to Send ACK?

- In-order segment arrival, no gaps, everything earlier already ACKed
  - Delayed ACK: wait up to 500ms, and then send ACK if nothing received
- In-order segment arrival, no gaps, one delayed ACK pending
  - Send one cumulative ACK
- Out-of-order arrival: Higher-than-expected sequence number, gap detected
  - Send ACK indicated the sequence number of the next expected byte
- Arrival of a segment that partially or completely fills a gap
  - Immediately send ACK if the segment starts at the lower end of the gap
