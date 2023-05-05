---
id: "Resource Record"
aliases:
  - "RDATA: A Function of RR Type"
tags:
  - "CS118"
---

- Name: List of labels
  - Label: Length ≤ 255, followed by $n$ chars
- Type: A, AAAA, ns, cname, MX, txt, PTR, ...
  - Many new types have been defined in recent years
- Time-to-live: Cache lifetime measured in seconds, determined by the DNS
  operator (in some master file)
- RDLENGTH: Resource data length

## RDATA: A Function of RR Type

- A: IPv4, AAAA: IPv6
  - Name: A DNS name
  - RDATA: IP address
- NS: An authoritative DNS name server for the named domain
  - Name: A domain name
  - RDATA: DNS server's name
- cname: A canonical name
  - Name: A canonical name
  - RDATA: The real DNS name
- MX: Mail server
  - Name: The domain name that runs the mail service
  - RDATA: 2-byte preference value + DNS name for mail server
- TXT: Any value in text format

## RRSET: Set of Resource Records

- DNS stores _multiple values_ of the same name, class, and type in multiple RRs
- All the RRs with the same name, type, and class
  - Forms the basic unit of a DNS response

## DNS Over TCP vs. UDP

- Over TCP, we have a minimum of 2 RTTs to get a response
- Over UDP
  - If there is no loss, the message is received in 1 RTT
  - If no reply is received after some pre-determined time, another
    authoritative server from the RRset is queried
