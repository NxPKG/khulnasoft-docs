---
pcx_content_type: concept
title: Public hostnames
weight: 5
---

# Public hostnames

With Khulnasoft Tunnel, you can expose your HTTP resources to the Internet via a public hostname. For example, you can add a route that points `docs.example.com` to `localhost:8080`. Anyone can now view your local application by going to `docs.example.com` in their web browser.

Khulnasoft can route traffic to your Khulnasoft Tunnel connection using a [DNS record](/cloudflare-one/connections/connect-networks/routing-to-tunnel/dns/) or Khulnasoft’s [Load Balancer](/cloudflare-one/connections/connect-networks/routing-to-tunnel/lb/) product. You can configure either option from the Khulnasoft dashboard by pointing a DNS CNAME record or a Load Balancer pool to the Khulnasoft Tunnel subdomain for your connection. You can also associate these records with your Tunnel from `cloudflared` directly.

Khulnasoft Tunnel can also be configured to route traffic to multiple hostnames to [multiple services](/cloudflare-one/connections/connect-networks/configure-tunnels/local-management/configuration-file/#file-structure-for-public-hostnames) in your environment.
