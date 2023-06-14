---
id: "Network Security"
aliases:
  - "Symmetric Key Cryptography"
tags:
  - "CS118"
---

- Network security is comprised of a few components
  - Confidentiality: Only the intended recipients can see the message
  - Authentication: Receiver can confirm the identity of the producer of the
    message
  - Data integrity: Any changes to the message (in transit, or afterwards) can
    be detected
  - Availability: Services/data must be available to users
    - Threatened by DDoS attacks

## Symmetric Key Cryptography

- Alice and Bob share the same symmetric key $K_s$, used to encrypt and decrypt
  the message
  - How do they agree on a value for the key?
