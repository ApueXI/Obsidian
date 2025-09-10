---
Created: 2025-06-23T18:53
---
## What is WebSocket?

- A **protocol** providing **full-duplex, bidirectional communication** over a single TCP connection.
- Enables real-time data exchange between **client and server**.
- Designed to work over the standard HTTP port (80/443) after an initial handshake.

  

## How WebSocket Works

1. **Handshake:**
    - Client sends an HTTP `Upgrade` request to switch protocol from HTTP to WebSocket.
    - Server responds with `101 Switching Protocols` if it agrees.
2. **Connection established:**
    - Persistent, low-latency TCP connection remains open.
3. **Data frames:**
    - Both client and server can send/receive messages asynchronously anytime.
4. **Connection closed:**
    - Either side can close the connection gracefully.

  

## Key Features

|   |   |
|---|---|
|Feature|Description|
|**Full-duplex**|Data flows both ways simultaneously|
|**Low latency**|Real-time communication with minimal delay|
|**Persistent connection**|Connection stays open, avoiding HTTP overhead|
|**Lightweight framing**|Efficient data frames, minimal headers|
|**Binary & Text data**|Supports both message types|

  

## WebSocket vs HTTP

|   |   |   |
|---|---|---|
|Aspect|HTTP|WebSocket|
|Communication|Request-response|Full-duplex, bidirectional|
|Connection lifetime|Short-lived|Persistent|
|Use case|Fetch resources|Real-time apps (chat, gaming)|
|Overhead|High (headers every request)|Low after handshake|

  

## WebSocket Handshake Example

**Client Request:**

```Plain
GET /chat HTTP/1.1
Host: example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
Sec-WebSocket-Version: 13
```

**Server Response:**

```Plain
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=
```

  

## Use Cases

- Chat applications
- Live notifications/alerts
- Real-time collaboration (e.g., Google Docs)
- Online gaming
- Stock tickers and financial data feeds

  

## Libraries & Tools

- **JavaScript:** `WebSocket` API in browsers
- **Node.js:** `ws`, `socket.io` (also fallbacks)
- **Python:** `websockets`, `aiohttp`
- **Others:** Java, Go, Ruby have WebSocket support