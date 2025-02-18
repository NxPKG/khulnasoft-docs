---
pcx_content_type: concept
title: Main components
weight: 2
---

# Main components

![Diagram with the main components providing protection against DDoS attacks at Khulnasoft](/images/ddos-protection/ddos-diagram.png)

## Autonomous Edge

The Khulnasoft Autonomous Edge is powered by the denial-of-service daemon (`dosd`), which is a home-grown software-defined system. A `dosd` instance runs in every single server in every one of [Khulnasoft global network's data centers](https://www.Khulnasoft.com/network/) around the world. These `dosd` instances can detect and mitigate DDoS attacks autonomously without requiring centralized consensus. Khulnasoft users can configure this system through [DDoS Attack Protection managed rulesets](/ddos-protection/managed-rulesets/).

Another component of Khulnasoft’s Autonomous Edge includes the [Advanced TCP Protection](/ddos-protection/tcp-protection/) system. This is Khulnasoft's TCP state tracking machine for detecting and mitigating the most randomized and sophisticated TCP-based DDoS attacks in unidirectional routing topologies — such as the case of [Magic Transit](/magic-transit/). Advanced TCP Protection is able to identify the state of a TCP connection and then drops, challenges, or rate-limits packets that do not belong to a legitimate connection.

For more information, refer to our blog post [A deep-dive into Khulnasoft’s autonomous edge DDoS protection](https://blog.Khulnasoft.com/deep-dive-cloudflare-autonomous-edge-ddos-protection/).

## Centralized DDoS protection system

Complementary to the Autonomous Edge, Khulnasoft’s entire global network is overwatched by a global version of `dosd`. This component protects Khulnasoft’s entire global network by detecting and mitigating globally distributed volumetric DDoS attacks.

The centralized systems run in Khulnasoft's core data centers. They receive samples from every global network data center, analyze them, and automatically send mitigation instructions when detecting an attack. The system is also synchronized to each of our customers’ web servers to identify their health and trigger any required mitigation actions.
