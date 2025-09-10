---
Created: 2025-06-23T18:52
---
## What is DNS?

- **DNS (Domain Name System)** translates human-friendly domain names (e.g., `example.com`) into IP addresses (e.g., `93.184.216.34`) that computers use to communicate.
- Acts like the **internet’s phonebook**.

  

## Why DNS?

- Humans remember names, not IP numbers.
- IPs can change, but domain names stay constant.
- Makes the web easier to navigate.

  

## Key Components of DNS

|   |   |
|---|---|
|Component|Description|
|**Domain Name**|The readable website address (e.g., `google.com`)|
|**DNS Resolver**|The client-side service that asks DNS servers to resolve names|
|**Root Nameserver**|Top-level DNS servers that direct queries to TLD servers|
|**TLD Nameserver**|Servers for Top-Level Domains (e.g., `.com`, `.org`)|
|**Authoritative Nameserver**|Final DNS server that holds the actual DNS records for the domain|
|**DNS Records**|Data entries (A, AAAA, CNAME, MX, TXT, etc.) for domains|

  

## DNS Resolution Process (Simplified)

1. **User enters URL** in browser.
2. **Browser asks DNS resolver** (usually provided by ISP).
3. **Resolver queries Root server** for the TLD server (e.g., `.com`).
4. **Resolver queries TLD server** for authoritative nameserver of the domain.
5. **Resolver queries Authoritative nameserver** for the domain’s IP address (A record).
6. **Resolver returns IP address** to the browser.
7. **Browser connects** to the server IP to load the site.

  

## Common DNS Record Types

|   |   |   |
|---|---|---|
|Record Type|Purpose|Example|
|**A**|Maps domain to IPv4 address|`example.com → 93.184.216.34`|
|**AAAA**|Maps domain to IPv6 address|`example.com → 2606:2800:220:1:248:1893:25c8:1946`|
|**CNAME**|Alias to another domain name|`www.example.com → example.com`|
|**MX**|Mail server for the domain|`mail.example.com`|
|**TXT**|Text data, often for verification or SPF|`v=spf1 include:_spf.google.com ~all`|

  

## DNS Caching

- DNS results are cached by resolvers and clients to speed up resolution.
- TTL (Time To Live) controls how long records are cached.
- Cache improves performance but can delay propagation of DNS changes.

  

## Summary

|   |   |
|---|---|
|Step|Action|
|1. URL entered|User types domain name|
|2. Resolver lookup|Resolver queries DNS hierarchy|
|3. Root → TLD → Authoritative|Stepwise query to find final IP address|
|4. IP returned|Resolver sends IP back|
|5. Browser connects|Browser loads website using IP|