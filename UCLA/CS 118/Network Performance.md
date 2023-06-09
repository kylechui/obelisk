---
id: "Network Performance"
aliases:
  - "Packet Switching: Store-and-Forward"
tags:
  - "CS118"
---

- Three basic measurements:
  - Throughput (bits/sec)
    - Over a single link, it's just the link bandwidth
    - Over multiple links, it's much harder to quantify
  - Loss rate (% of packets lost)
    - Wired links had loss due to transmission or congestion
    - Wireless links have limited transmission rate, a higher bit error rate
      than wired, and a high variance in the number of hosts
  - Delay (msec)
    - Four sources of delay:
      - Node processing: checking for bit errors, determining output link
      - Transmission of the packet: packet length / link bandwidth
      - Propagation of the packet: physical length of link / propagation speed
        in medium
      - Queueing: number of packets in queue $\cdot$ transmission time per
        packet

## Packet Switching: Store-and-Forward

- The entire packet must arrive at the router before it can start to be
  transmitted to the next link
