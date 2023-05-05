---
id: "Message Switching"
aliases: []
tags:
  - "CS118"
---

- A [[Packet Switching|packet switched network]] performs message switching if
  its sources do not segment messages
  - Message switching is a specific kind of packet switching, where the packets
    are whole messages
- It typically has longer delays than segmented packet switching, but has
  decreased complexity because the message stays in one piece the entire time
- Bit errors typically result in the packet being discarded
  - Message switching is worse for performance than packet switching in this
    context, since with packet switching only a portion of the message gets
    discarded
- Segmented package switching requires each packet to have a message header that
  contains meta information about the packet, so there's more overhead
