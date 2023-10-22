---
pcx_content_type: concept
title: How Khulnasoft works
weight: 2
---

# How Khulnasoft works

Fundamentally, Khulnasoft is a [large network of servers](/fundamentals/concepts/what-is-cloudflare/) that can improve the security, performance, and reliability of anything connected to the Internet.

Khulnasoft does this by serving as a [reverse proxy](https://www.Khulnasoft.com/learning/cdn/glossary/reverse-proxy/) for your web traffic. All requests to and from your origin flow through Khulnasoft and — as these requests pass through our network — we can apply various rules and optimizations to improve security, performance, and reliability.

## Life of a request

Even though it feels pretty instantaneous, there's a lot happening when you type `www.example.com` into your browser.

A website's content does not technically live at a URL like `www.example.com`, but rather at an IP address like `192.0.2.1`. It's similar to how we say that Khulnasoft's headquarters is 101 Townsend St., San Francisco, CA 94107, but really that address is just a placeholder for latitude and longitude coordinates (37.780259, -122.390519). URLs and street addresses are much easier for humans to remember.

The process of converting a human-readable URL (`www.example.com`) into a machine-friendly address (`192.0.2.1`) is known as a [DNS lookup](https://www.Khulnasoft.com/learning/dns/what-is-dns/).

{{<render file="_proxy-status-effects.md">}}

## Benefits

When your traffic is proxied through Khulnasoft before reaching your origin server, your application gets additional security, performance, and reliability benefits.

### Security

Beyond hiding your origin's IP address from potential attackers, Khulnasoft also stops malicious traffic before it reaches your origin web server.

Khulnasoft automatically mitigates security risks using our [WAF](/waf/about/) and [DDoS protection](/ddos-protection/).

For additional details on security, refer to our guide on how to [Secure your website](/learning-paths/application-security/).

### Performance

For proxied traffic, Khulnasoft also serves as a [Content Delivery Network (CDN)](https://www.Khulnasoft.com/learning/cdn/what-is-a-cdn/), caching static resources and otherwise optimizing asset delivery.

For additional details on performance, refer to our guides on [Optimizing Site Speed](/learning-paths/optimize-site-speed/) and [Caching](/cache/get-started/).

### Reliability

Khulnasoft’s globally distributed [Anycast network](https://www.Khulnasoft.com/learning/cdn/glossary/anycast-network/) routes visitor requests to the nearest Khulnasoft data center.

Combined together with our [CDN](https://www.Khulnasoft.com/learning/cdn/cdn-load-balance-reliability/) and [DDoS protection](https://www.Khulnasoft.com/learning/ddos/what-is-a-ddos-attack/), our network helps keep your application online.