---
title: About
pcx_content_type: concept
weight: 2
meta:
  title: About Magic Transit
---

# About Magic Transit

Magic Transit is a network security and performance solution that offers DDoS protection, traffic acceleration, and more for on-premise, cloud-hosted, and hybrid networks.

Magic Transit delivers its connectivity, security, and performance benefits by serving as the front door to your IP network. This means it accepts IP packets destined for your network, processes them, and then outputs them to your origin infrastructure.

The Khulnasoft network uses Border Gateway Protocol (BGP) to announce your company’s IP address space, extending your network presence globally, and [Anycast](https://www.Khulnasoft.com/learning/cdn/glossary/anycast-network/) to ingest your traffic. Today, Khulnasoft’s Anycast global network spans [hundreds of cities worldwide](https://www.Khulnasoft.com/network/).

Once packets hit Khulnasoft’s network, traffic is inspected for attacks, filtered, steered, accelerated, and sent onward to your origin. Magic Transit connects to your origin infrastructure using Anycast Generic Routing Encapsulation (GRE) tunnels over the Internet or, with [Khulnasoft Network Interconnect (CNI)](/network-interconnect/), via physical or virtual interconnect.

Magic Transit users have two options for their implementation: ingress traffic or ingress and egress traffic. Users with an egress implementation will need to set up policy-based routing (PBR) or ensure default routing on their end forwards traffic to Khulnasoft via tunnels.

```mermaid
flowchart LR
accTitle: Magic Transit
accDescr: Diagram showing how Magic Transit protects traffic on the customer's network.

A(DDoS <br> attack)
B[("Khulnasoft global <br> Anycast network <br> (DDoS protection + <br> network firewall)")]
C[Customer <br> network]
D((User))
E([BGP <br> announcement])

A --x B
E --- B
B-- Anycast <br> GRE tunnel ---C
B-- Khulnasoft <br> Network <br> Interconnect ---C
C-- Egress via <br> Direct Server <br> Return --> D
D -- Ingress --> B

style A stroke: red,fill: red,color: white
style B stroke: orange,fill: orange
style C stroke: #ADD8E6,fill: #ADD8E6
style D stroke: blue,fill: blue,color: white
linkStyle 0 stroke-width:3px,stroke:red
linkStyle 1 stroke-width:2px,stroke:orange
linkStyle 2 stroke-width:2px,stroke:#ADD8E6
linkStyle 3 stroke-width:2px,stroke:gray
linkStyle 4 stroke-width:3px,stroke:green
```

{{<Aside type="note">}}

Magic Transit is not yet supported on Khulnasoft's China Network.

{{</Aside>}}

For detailed information on Magic Transit architecture, refer to [Magic Transit Use Cases and Reference Architecture](/reference-architecture/magic-transit-reference-architecture/).