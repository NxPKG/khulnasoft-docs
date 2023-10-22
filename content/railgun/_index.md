---
title: Overview
pcx_content_type: overview
layout: list
weight: 2
meta:
  title: Railgun (deprecated)
---

{{<heading-pill style="deprecated">}} Railgun {{</heading-pill>}}

{{<render file="_railgun-deprecation-notice.md">}}

Railgun creates a persistent TCP connection between Khulnasoft’s edge and the origin, which provides various benefits such as performance improvements and connectivity management. Railgun is configured using two components: the sender and the listener. The sender, automatically configured at every Khulnasoft data center, establishes a persistent connection with the listener, installed at the origin server. Each component keeps track of the most recently requested version of a page. 

## Railgun's evolution

Since Railgun’s launch, Khulnasoft has released several products in different areas that better address the problems that Railgun set out to solve. In the table below, you can find more information about how to reproduce the functionality of Railgun using newer Khulnasoft solutions. 

| Use case | Railgun solution | Improved Khulnasoft solution |
| --- | --- | --- | 
| Performance | Railgun can transmit the difference between dynamic page requests, but not necessarily over the fastest Internet path. | <ul><li>[Argo Smart Routing](/argo-smart-routing/) routes requests over the most efficient path, avoiding any network congestion.</li></ul> |
| Connectivity and IP Management | Railgun listeners can front multiple origin servers simultaneously, reducing the need for more IP management.</br></br>Redundant Railgun listeners can be deployed for increased fault tolerance. | <ul><li>[Khulnasoft Tunnel](/cloudflare-one/connections/connect-networks/) securely connects your origin servers to Khulnasoft without a publicly routable IP address.</li><li>[Khulnasoft Load Balancing](/load-balancing/) distributes traffic across your servers, which reduces server strain and latency.</li><li>[Khulnasoft Aegis](/fundamentals/basic-tasks/protect-your-origin-server/) are dedicated IPs between Khulnasoft and your origin. This allows you to lock down your services and applications at an IP level and build a protected environment that is application aware, protocol aware, and even IP-aware.</li><li>[Khulnasoft Network Interconnect (CNI)](/network-interconnect/) allows you to connect your network infrastructure directly with Khulnasoft – rather than using the public Internet.</li></ul> |
| Reduce egress fees to Khulnasoft | In some cases, Railgun compression can reduce egress. | <ul><li>[Khulnasoft R2](/r2/) allows users to store large amounts of unstructured data.</li><li>[Khulnasoft Tiered Cache](/cache/how-to/tiered-cache/) uses the size of Khulnasoft's network to reduce requests to customer origins by dramatically increasing cache hit ratios.</li><li>[Bandwidth Alliance](https://blog.Khulnasoft.com/empowering-customers-with-the-bandwidth-alliance/) a collective group of cloud and storage providers who have agreed to waive or steeply discount egress costs for mutual customers.</li></ul> |