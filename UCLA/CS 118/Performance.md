---
id: "Performance"
aliases: []
tags:
  - "CS 118"
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
      - Transmission of the packet: link bandwidth / packet length
      - Propagation of the packet: physical length of link / propagation speed
        in medium
      - Queueing: number of packets in queue $\cdot$ transmission time per
        packet
