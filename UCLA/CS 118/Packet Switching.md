---
id: "Packet Switching"
aliases: []
tags:
  - "CS118"
---

- Statistical multiplexing
  - Each node sends packets as soon as link available
  - Receiver gets a full packet first, then forwards it towards the destination
  - Store-and-forward
  - Packet switch can temporarily buffer up packets
    - This introduces delay
    - Packets can get dropped when the queue is full
