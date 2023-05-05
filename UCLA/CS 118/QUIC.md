---
id: "QUIC"
aliases:
  - "Problems with HTTP/1.1"
tags:
  - "CS118"
---

- The primary goal is for HTTP to run faster
  - While software doesn't "wear out", requirements do change

## Problems with HTTP/1.1

- Head-of-line blocking: Requests are handled sequentially, and a large request
  will block sequential requests
  - Solution: Use multiple connections
- Large header: ASCII is used for the header, and repetitive information is
  encoded in each query

## HTTP/2.0

- Message: Either an HTTP request or response
  - Encoded in one (or more) frames
- Frame: The basic communication unit, uniquely identifiable
- Stream: A virtual channel with priority, carrying frames in both directions
  - One stream is used for each request/response pair

## Benefits of HTTP/2.0

- Reduces HTTP header overhead, since it uses binary encoding and compresses the
  header
- A single TCP connection is created between each client/server pair
  - Multiple streams are used, one for each request/reply pair
  - Large messages are broken down into multiple frames
  - Frames from all streams can be interleaved
    - We hope that the last two help prevent head-of-line blocking

## Problems with TCP

- Connection ID is tied to IP address (not great for mobile devices)
- Congestion control is tangled with the window flow control for reliable
  delivery
  - Congestion window: Controls the number of packets inside the network
  - Any lost packet blocks the congestion window from moving forwards
- Connection setup delay
  - TCP connection setup, and then TLS setup

## QUIC: 4 Major Components

- Transport connection management
- Data delivery
  - Streams: Multiplexing inside a single QUIC connection
  - Frames: Packaging into next outgoing QUIC packet based on priority
- Decou

## QUIC Terminology

- Connection: Conversation between two QUIC endpoints
  - Multiple streams multiplexed in a single connection
- Stream: A single or bi-directional byte stream delivery within a QUIC
  connection
  - Each is identified by a stream ID, established by either end
  - Each stream can carry multiple frames
- Frame: Basic unit of transmission
  - QUIC defines multiple types of frames; we focus on stream frames and ACK
    frames
- Packet: A unstructured UDP payload
  - One UDP datagram can encapsulate multiple QUIC packets
  - Each packet can contain multiple frames

## QUIC Packet: Container of Frames

- Each data stream frame contains the stream ID, sequence number
  - Frames from the same packet may be in different streams
- ACK frame acknowledges QUIC packets (not QUIC stream frames)

## QUIC Packet Number

- Each QUIC packet carries a monotonically increasing packet number
- QUIC packet number is used for loss detection
- There is no retransmission in QUIC
  - Lost stream frames are put into the next outgoing packet to be retransmitted

## Information Carried in ACK Frame

- The largest packet number $P_n$ received
  - Together with the packet numbers of _all recently received_ QUIC packets,
    encoded in ACK blocks
