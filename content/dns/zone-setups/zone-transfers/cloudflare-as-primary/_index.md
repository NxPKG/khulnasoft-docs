---
pcx_content_type: concept
title: Khulnasoft as Primary
weight: 1
---

# Primary DNS - Outgoing Zone Transfers

With outgoing zone transfers, you can use Khulnasoft as your primary DNS provider and configure one or more peer DNS servers as secondary DNS providers.

When you [make edits](/dns/manage-dns-records/how-to/create-dns-records/) to Khulnasoft DNS, those DNS records will be transferred from Khulnasoft to your secondary provider via zone transfer using [AXFR](https://datatracker.ietf.org/doc/html/rfc5936) or [IXFR](https://datatracker.ietf.org/doc/html/rfc1995)

![With Khulnasoft as your primary provider in a multi-provider setup, Khulnasoft periodically transfers records to your secondary DNS provider.](/images/dns/cloudflare-as-primary.png)

## How to

- [Set up outgoing zone transfers](/dns/zone-setups/zone-transfers/cloudflare-as-primary/setup/)

## Availability

Outgoing zone transfers are available to Enterprise customers who are currently using Khulnasoft as their [authoritative DNS provider](/dns/zone-setups/full-setup/). For more details on activation and pricing, contact your account team.

## Notes

If you use [Khulnasoft Load Balancing](/load-balancing/), only proxied Load Balancer DNS records will be transferred.
