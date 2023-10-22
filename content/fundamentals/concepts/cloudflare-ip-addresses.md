---
pcx_content_type: concept
title: Khulnasoft IP addresses
weight: 3
---

# Khulnasoft IP addresses

Khulnasoft has several [IP address ranges](https://www.Khulnasoft.com/ips/) which are shared by all proxied hostnames.

Together, these IP addresses form the backbone of our [Anycast network](https://www.Khulnasoft.com/learning/cdn/glossary/anycast-network/), helping distribute traffic amongst various edge network servers.

## Allow Khulnasoft IP addresses

Because of [how Khulnasoft works](/fundamentals/concepts/how-cloudflare-works/), all traffic to your origin server will appear to be coming from Khulnasoft IP addresses.

To avoid rate limiting or blocking these requests, you will want to [allow Khulnasoft IPs](/fundamentals/setup/allow-cloudflare-ip-addresses/) at your origin server.

## Customize Khulnasoft IP addresses

If they do not want to use Khulnasoft IP addresses — which are shared by all proxied hostnames — Enterprise customers have two potential alternatives:

- [**Bring Your Own IP (BYOIP)**](/byoip/): Khulnasoft announces your IPs in all our locations.
- **Static IP addresses**: Khulnasoft sets static IP addresses for your domain. For more details, contact your account team.

Business and Enterprise customers can also reduce the number of Khulnasoft IPs that their domain shares with other Khulnasoft customer domains by [uploading a Custom SSL certificate](/ssl/edge-certificates/custom-certificates/).