---
Created: 2025-06-23T18:50
---
## What is Client-Server Architecture?

A design model where **clients** (users or devices) request services or resources from **servers** (centralized machines or programs).

  

## Key Components

|   |   |
|---|---|
|Component|Role|
|**Client**|Sends requests and consumes services (e.g., browsers, apps)|
|**Server**|Receives requests, processes them, and sends back responses|

  

## How It Works

1. **Client sends a request** to the server (e.g., HTTP request).
2. **Server processes the request**, performs operations (e.g., fetch data).
3. **Server sends a response** back to the client.
4. **Client processes the response** and displays or uses the data.

  

## Characteristics

- **Separation of concerns:** Client focuses on user interface; server handles data/storage/logic.
- **Scalability:** Servers can serve multiple clients simultaneously.
- **Stateless communication:** Typically, each request is independent (especially in HTTP).
- **Centralized control:** Server controls resources and security.

  

## Examples

|   |   |
|---|---|
|Example|Description|
|Web browsing|Browser (client) requests HTML pages from web server|
|Email|Email client requests/sends emails via mail server|
|APIs|Client apps request data from API servers|

  

## Advantages

- Centralized management and control.
- Easier to update and maintain server-side logic.
- Supports multiple client types (mobile, web, desktop).

  

## Disadvantages

- Server can become a bottleneck if overloaded.
- Requires reliable network connection.
- Single point of failure if server crashes (unless load-balanced).