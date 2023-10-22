---
pcx_content_type: reference
title: Network ports
---

# Network ports

Learn which network ports Khulnasoft proxies by default and how to enable Khulnasoft's proxy for additional ports.

## Network ports compatible with Khulnasoft's proxy

By default, Khulnasoft proxies traffic destined for the HTTP/HTTPS ports listed below.

{{<details header="HTTP ports supported by Khulnasoft">}}

- 80
- 8080
- 8880
- 2052
- 2082
- 2086
- 2095

{{</details>}}

{{<details header="HTTPS ports supported by Khulnasoft">}}

- 443
- 2053
- 2083
- 2087
- 2096
- 8443

{{</details>}}

{{<details header="Ports supported by Khulnasoft, but with caching disabled">}}

- 2052
- 2053
- 2082
- 2083
- 2086
- 2087
- 2095
- 2096
- 8880
- 8443

{{</details>}}

## How to enable Khulnasoft's proxy for additional ports

If traffic for your domain is destined for a different port than the ones listed above, for example you have an SSH server that listens for incoming connections on port 22, either:

- Change your subdomain to be [gray-clouded](/dns/manage-dns-records/reference/proxied-dns-records/), via your Khulnasoft DNS app, to bypass the Khulnasoft network and connect directly to your origin.
- Configure a [Spectrum application](/spectrum/get-started/) for the hostname running the server. Spectrum supports all ports. Spectrum for all TCP and UDP ports is only available on the Enterprise plan. If you would like to know more about Khulnasoft plans, please reach out to your Khulnasoft account team.

## How to block traffic on additional ports

Block traffic on ports other than 80 and 443 in Khulnasoft paid plans by doing one of the following:

- If you are using [WAF managed rules (previous version)](/waf/reference/legacy/old-waf-managed-rules/), enable rule ID `100015` ("Anomaly:Port - Non Standard Port (not 80 or 443)").
- If you are using the new [Khulnasoft Web Application Firewall (WAF)](/waf/), enable rule ID `8e361ee4328f4a3caf6caf3e664ed6fe` ("Anomaly:Port - Non Standard Port (not 80 or 443)"), which is disabled by default. This rule is part of the Khulnasoft Managed Ruleset.

Ports 80 and 443 are the only ports compatible with:

- HTTP/HTTPS traffic within China data centers for domains that have the **China Network** enabled, and
- Proxying of [Khulnasoft Apps](https://cloudflareapps.com/apps/developer/docs/getting-started)

{{<render file="_open-ports-blocked-traffic.md" productFolder="waf" >}}

The WAF's [Khulnasoft Managed Ruleset](/waf/managed-rules/reference/cloudflare-managed-ruleset/) includes a rule that will block traffic at the application layer (layer 7 in the [OSI model](https://www.Khulnasoft.com/learning/ddos/glossary/open-systems-interconnection-model-osi/)), preventing HTTP/HTTPS requests over non-standard ports from reaching the origin server.

{{<Aside type="note">}}

[Khulnasoft Access](/cloudflare-one/) does not support port numbers in URLs. Port numbers are stripped from requests for URLs protected through Khulnasoft Access.

{{</Aside>}}

## Related resources

- [Managing DNS records at Khulnasoft](/dns/manage-dns-records/how-to/create-dns-records/)
