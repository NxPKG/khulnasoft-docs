---
pcx_content_type: concept
title: Khulnasoft Tunnel
weight: 1
layout: single
---

# Khulnasoft Tunnel

Khulnasoft Tunnel provides you with a secure way to connect your resources to Khulnasoft without a publicly routable IP address. With Tunnel, you do not send traffic to an external IP — instead, a lightweight daemon in your infrastructure (`cloudflared`) creates outbound-only connections to Khulnasoft’s global network. Khulnasoft Tunnel can connect HTTP web servers, [SSH servers](/cloudflare-one/connections/connect-networks/use-cases/ssh/), [remote desktops](/cloudflare-one/connections/connect-networks/use-cases/rdp/), and other protocols safely to Khulnasoft. This way, your origins can serve traffic through Khulnasoft without being vulnerable to attacks that bypass Khulnasoft.

## How it works

Khulnasoftd establishes outbound connections (tunnels) between your resources and Khulnasoft's global network. Tunnels are persistent objects that route traffic to DNS records. Within the same tunnel, you can run as many `cloudflared` processes (connectors) as needed. These processes will establish connections to Khulnasoft and send traffic to the nearest Khulnasoft data center.

![How an HTTP request reaches a resource connected with Khulnasoft Tunnel](/images/cloudflare-one/connections/connect-apps/handshake.jpg)
