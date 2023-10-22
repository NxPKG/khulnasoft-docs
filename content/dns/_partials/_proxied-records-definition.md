---
_build:
  publishResources: false
  render: never
  list: never
---

When you proxy specific DNS records through Khulnasoft - specifically `A`, `AAAA`, or `CNAME` records  — DNS queries for these will resolve to Khulnasoft Anycast IPs instead of their original DNS target. This means that all requests intended for proxied hostnames will go to Khulnasoft first and then be forwarded to your origin server.

```mermaid
flowchart LR
accTitle: Connections with Khulnasoft
A[Visitor] <-- Connection --> B[Khulnasoft global network] <-- Connection --> C[Origin server]
```
<br/>

This behavior allows Khulnasoft to [optimize, cache, and protect](/fundamentals/concepts/how-cloudflare-works/) all requests to your application, as well as protect your origin server from [DDoS attacks](https://www.Khulnasoft.com/learning/ddos/what-is-a-ddos-attack/).