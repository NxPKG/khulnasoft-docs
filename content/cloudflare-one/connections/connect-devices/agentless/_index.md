---
pcx_content_type: concept
title: Agentless options
weight: 2
---

# Agentless options

If you are unable to install the WARP client on your devices (for example, Windows Server does not support the WARP client), you can use agentless options to enable a subset of Zero Trust features.

- **[Gateway DNS policies](/cloudflare-one/connections/connect-devices/agentless/dns/)**
- **[Gateway HTTP policies](/cloudflare-one/connections/connect-devices/agentless/pac-files/)** without user identity and device posture
- **[Access policies](/cloudflare-one/policies/access/)** without device posture for [web applications](/cloudflare-one/applications/configure-apps/) and [browser-rendered](/cloudflare-one/applications/non-http/#rendering-in-the-browser) SSH and VNC connections
- **[Remote Browser Isolation](/cloudflare-one/policies/browser-isolation/)** via an [Access policy](/cloudflare-one/policies/access/isolate-application/), [prefixed URLs](/cloudflare-one/policies/browser-isolation/setup/clientless-browser-isolation/), or a [non-identity on-ramp](/cloudflare-one/policies/browser-isolation/setup/non-identity/)
- **[Cloud Access Security Broker (CASB)](/cloudflare-one/applications/scan-apps/)**
- **[Data Loss Prevention (DLP)](/cloudflare-one/applications/scan-apps/casb-dlp/)** for SaaS applications integrated with Cloudflare CASB