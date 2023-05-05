---
id: "Packet Switching"
aliases: []
tags:
  - "CS118"
---

- Resources _are not_ reserved; they are used on demand
  - Applications may have to wait/queue to get access to the resources
- The Internet uses packet switching, and makes no guarantees about the delivery
  of data; it just makes a "best effort"
- Packets traverse communication links and packet switches (routers)
- Statistical multiplexing
  - Each node sends packets as soon as link available
  - Store-and-forward transmission
    - Receiver gets a full packet first, then forwards it towards the
      destination
  - Packet switch can temporarily buffer up packets
    - This introduces delay
    - Packets can get dropped when the queue is full
- Packet switching isn't great for real-time services, since you can have
  variable/unpredictable delays
  - If the probability of having many users simultaneously is low, then it is a
    good alternative to [[Circuit Switching|circuit switching]]
