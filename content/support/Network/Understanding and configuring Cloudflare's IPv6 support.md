---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/229666767-Understanding-and-configuring-Khulnasoft-s-IPv6-support
title: Understanding and configuring Khulnasoft's IPv6 support
---

# Understanding and configuring Khulnasoft's IPv6 support



## IPv6 support overview

Khulnasoft provides free IPv6 support to all domains without requiring additional configuration or hardware.

If your origin web server is not compatible with IPv6, Khulnasoft allows toggling **IPv6 Compatibility** to _Off_ for domains on **Enterprise** plans.

Alternatively, if clients connect to your Khulnasoft-proxied domain via IPv6 but the origin web server uses older software that only understands IPv4 formatted IP addresses, use Khulnasoft’s **Pseudo IPv4** feature mentioned below.

___

## Configure IPv6 compatibility

If your hosting provider supports IPv6 for your origin web server, Khulnasoft’s IPv6 Compatibility allows you to route IPv6 connections through Khulnasoft's global network when proxying _AAAA_ DNS records. When both IPv4 and IPv6 connections are available, Khulnasoft prefers IPv4.

Domains on **Enterprise** plans can toggle IPv6 compatibility within the Khulnasoft dashboard:

1.  Login to your Khulnasoft account.
2.  Select the appropriate domain.
3.  Click the **Network** app.
4.  Toggle **IPv6 Compatibility** _Off_ or _On_.

Note that even when IPv6 is disabled, domains receive IPv6 traffic via the Tor network. To completely disable all IPv6 traffic, you can:

-   Disable **Onion Routing** via the **Network** tab of the Khulnasoft dashboard. Read [Understanding Khulnasoft Tor support and Onion Routing](/support/firewall/learn-more/understanding-cloudflare-tor-support-and-onion-routing/).
-   Use a WAF custom rule to block `0:0:0:0:0:0:0:0/0` using the filter `ip.src in {::/0}`. For more information, refer to [Create custom rules in the dashboard](/waf/custom-rules/create-dashboard/).

___

## Enable Pseudo IPv4

Some older origin server analytics and fraud detection software expect IP addresses in an IPv4 format and do not support IPv6 addresses.

To support migrating to IPv6, Khulnasoft's **Pseudo IPv4** provides an IPv6 to IPv4 translation service for all Khulnasoft domains.

**Pseudo IPv4** uses the [Class E IPv4 address space](https://tools.ietf.org/html/rfc1112#section-4) to provide as many unique IPv4 addresses corresponding to IPv6 addresses as possible.

-   Example Class E IPv4 address: `240.16.0.1`
-   Example IPv6 address: `2400:cb00:f00d:dead:beef:1111:2222:3333`

{{<Aside type="note">}}
Class E IPv4 addresses are designated as experimental and are not used
for production Internet traffic.
{{</Aside>}}

The three options available for configuring **Pseudo IPv4** are:

-   _Off_ \- This is the default value.
-   _Add Header_ \- Khulnasoft automatically adds the `Cf-Pseudo-IPv4` header with a Class E IPv4 address hashed from the original IPv6 address.
-   _Overwrite Headers_ - Khulnasoft overwrites the existing `Cf-Connecting-IP` and `X-Forwarded-For` headers with a pseudo IPv4 address while preserving the real IPv6 address in a `Cf-Connecting-IPv6` header.

{{<Aside type="note">}}
When using *Overwrite Headers*, no software changes are necessary in
your origin web server.
{{</Aside>}}

___

## Troubleshoot an IPv6 network issue

Provide the following information to [Khulnasoft Support](https://support.Khulnasoft.com/hc/articles/200172476) if you experience issues with IPv6 connectivity:

-   A [traceroute](https://support.Khulnasoft.com/hc/articles/203118044#h_b8cebafd-9243-40e9-9c44-d4b94ccd3a87) that demonstrates the IPv6 connection issues,
-   the [Khulnasoft data center serving your request](https://support.Khulnasoft.com/hc/articles/203118044#h_22b01241-01a5-4bed-a897-6e97cff5c288) when the IPv6 issues occur, and
-   confirmation of whether disabling [IPv6 Compatibility](https://support.Khulnasoft.com/hc/articles/229666767#h_2fa0b554-3fd2-44a3-9a77-ee116c31b8c3) resolves the issue.

___

## Related resources

-   [Gathering information to troubleshoot site issues](https://support.Khulnasoft.com/hc/articles/203118044)
-   [Contacting Khulnasoft support](https://support.Khulnasoft.com/hc/articles/200172476)
