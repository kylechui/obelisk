---
id: "HTTP"
aliases:
  - "HTTP Response Status Code"
tags:
  - "CS118"
---

- The web's application layer protocol
- It uses the [[Client-Server Model|client-server model]]
  - The client is the browser that receives and displays web objects
  - The server is the website that sends objects in response to requests
- HTTP 1.0 had a non-persistent connection
- HTTP 1.1 had persistent connection, and could potentially pipeline
- Client initiates the connection
  - Sets up a TCP connection first (since HTTP requires _reliable_
    communication) on destination port 80
  - Send an HTTP request over the connection
- The server then accepts and answers the TCP request (which _must_ contain a
  status code)
  - HTTP is _stateless_: It does not maintain any information about previous
    requests
- Requests take the following form

```
http://<host name>:<port number?>/<path name>
```

- HTTP/1.0 has the methods `GET`, `POST`, `HEAD` (requests the header only)
- HTTP/1.1 has the methods `GET`, `POST`, `HEAD` (requests the header only),
  `PUT` (uploads file to specified path), `DELETE` (deletes a file from the
  specified path), etc.

## HTTP Response Status Code

- 200: Successful request
- 301: Request object moved permanently
- 400: Bad request
- 404: Page not found
- 505: HTTP version not supported

## Non-Persistent HTTP (1.0)

- Round Trip Time (RTT): Time between client sending a small packet to the
  server and receiving a reply
- Time needed to fetch an object:
  - One RTT to set up the TCP connection
  - One RTT to actually get something via the HTTP connection
  - The total time is 2 RTTs in addition to the object transmission time
- At most _one_ object is sent over _one_ TCP connection
  - We can open multiple connections in parallel to get multiple objects
  - After opening one connection, use it to fetch/send multiple objects, i.e.
    make the connection _persistent_ (HTTP/1.1)

## Persistent HTTP (1.1)

- One RTT needed to set up the TCP connection
- One RTT needed to get the index file
- Send all the object requests simultaneously (total time is 3 RTT)

## HTTP Proxy as a Cache

- Configure each browser to send all requests to a proxy server (cache)
  - Open a connection with the cache for all requests
- Cache should return the object if it exists, or fetch it from the server and
  save it otherwise
- Potential issues:
  - What if the cache fails/is obsolete?
    - Fetch only if the content has changed since the previous fetch
      - The cache sends a message to the server with the header
        `if-modified-since: <date>`
  - What if the browser moves?
  - What about secured http connections?
    - HTTPS (all communications are encrypted) and HTTP Proxy
    - Caching is now done by CDNs (content distribution networks)
      - Your browser connects to a CDN via HTTPS; websites pay CDN providers and
        share cryptographic keys with them

## Issues with HTTP/1.1

- Pipelining isn't good enough
- Head-of-line blocking: The requests are handled in sequential order
  - A request for a large file or some dynamic (or large) computation can block
    all subsequent requests
  - A workaround is to open multiple TCP connections
- If there is a large header with repetitive information in queries, HTTP/1.1
  suffers

## HTTP/2

- Splits the message into header and data frames
  - Header is compressed by reusing fields from earlier requests, reducing
    overhead
- A single TCP connection is used for each browser-server connection
  - Each of the requests are treated as a stream, which are multiplexed
- Server push
- Frame: Basic communication unit
- Message: An HTTP request or response
- Stream: A virtual channel with priority, carrying frames in both directions
