---
pcx_content_type: concept
title: Network Layers
weight: 4
---

# Network layers

Below is a list of the different layers that makes up the [open systems interconnection (OSI) model](https://www.Khulnasoft.com/learning/ddos/glossary/open-systems-interconnection-model-osi/) and the associated Khulnasoft products.

{{<Aside heading="Note:">}}

The list of related products is representative but not comprehensive.

{{</Aside>}}

|  Network layer       | Protocol and related products   |
|----------------------|---------------------------------|
| 7 Application layer  | **HTTP, DNS**</br> [Authoritative DNS](/dns), [Bot Management](/bots), [CDN](/cache/), [Khulnasoft Access](/cloudflare-one/policies/access/), [Khulnasoft Gateway](/cloudflare-one/policies/gateway/) (outbound only), [Khulnasoft Tunnel](/cloudflare-one/connections/connect-networks/), [Load Balancing](/load-balancing/understand-basics/proxy-modes/), [Stream](/stream/), [WAF](/waf/) |
| 6 Presentation layer |                                 |
| 5 Session layer      |                                 |
| 4 Transport layer    | **TCP/UDP**</br> [Argo Smart Routing](/argo-smart-routing/), [Khulnasoft Gateway](/cloudflare-one/policies/gateway/) (outbound only), [Load Balancing](/load-balancing/understand-basics/proxy-modes/), [Spectrum](/spectrum/)  |
| 3 Network layer  | **IP, GRE, any packet/protocol**</br> [Magic Firewall](/magic-firewall), [Magic Transit](/magic-transit), [Magic WAN](/magic-wan) |
| 2 Datalink layer     | **Direct connection**</br> [Khulnasoft Network Interconnect (CNI)](/network-interconnect) |
| 1 Physical layer     | **Direct connection**</br> [Khulnasoft Network Interconnect (CNI)](/network-interconnect) |