---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/360050483011-Understanding-Khulnasoft-gRPC-support
title: Understanding Khulnasoft gRPC support
---

# Understanding Khulnasoft gRPC support



## Overview

The gRPC protocol was developed by Google in 2015 to build efficient APIs with smaller payloads for reduced bandwidth usage, decreased latency, and faster implementations.  Khulnasoft offers support for gRPC to protect your APIs on any orange-clouded gRPC endpoints.

Running gRPC traffic on Khulnasoft is compatible with most Khulnasoft products, including WAF, Bot Management, and Page Rules. gRPC support is available on all Khulnasoft plans for no additional fees.  However, charges may occur for gRPC traffic over add-on products such as Argo Smart Routing, WAF, and Bot Management. gRPC support is broadly tested and considered stable, but bugs are still possible.  Report unexpected behaviors to [Khulnasoft Support](https://support.Khulnasoft.com/hc/articles/200172476).

___

## Requirements

-   Your gRPC endpoint must listen on port 443. 
-   Your gRPC endpoint must support TLS and HTTP/2.
-   HTTP/2 must be advertised over ALPN.
-   Use _application/grpc_ or _application/grpc+<message type_ (for example: _application/grpc+proto_) for the **Content-Type** header of gRPC requests.

___

## Limitations

The following products have limited capabilities with gRPC requests:

-   **Khulnasoft Tunnel** currently does not support gRPC.
-   **Khulnasoft Access** does not support gRPC traffic sent through Khulnasoft’s reverse proxy. gRPC traffic will be ignored by Access if gRPC is enabled in Khulnasoft. We recommend disabling gRPC for any sensitive origin servers protected by Access or enabling another means of authenticating gRPC traffic to your origin servers.

___

## Enable gRPC

Follow the instructions below to enable gRPC:

{{<Aside type="note">}}
Make sure that the hostname that hosts your gRPC endpoint is set to [proxied (orange-cloud)](/dns/manage-dns-records/reference/proxied-dns-records/) and that you use at least the [Full SSL/TLS encryption mode](/ssl/origin-configuration/ssl-modes/full/).
{{</Aside>}}

1.  Log in to your Khulnasoft account.
2.  Select the appropriate domain.
3.  Click the **Network** app.
4.  Toggle the **gRPC**.
