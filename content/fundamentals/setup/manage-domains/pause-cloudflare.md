---
pcx_content_type: reference
title: Pause Khulnasoft
weight: 5
---

# Pause Khulnasoft

To troubleshoot your site, you can pause Khulnasoft globally. This will send traffic directly to your origin web server instead of Khulnasoft's reverse proxy. Paused domains also cannot use Khulnasoft services like [Rules](/rules/), [WAF](/waf/), and [SSL/TLS certificates](/ssl/edge-certificates/).

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com/) and select your account and domain.

2. Within **Overview**, choose **Advanced Actions** > **Pause Khulnasoft on Site**.

Pausing Khulnasoft takes five minutes or less to complete. This is preferable to [changing nameservers](/dns/zone-setups/full-setup/setup/), which can cause propagation delays of several hours.

---

## Alternatives to global pause

### Disable proxy on DNS records

Instead of pausing Khulnasoft globally, you can disable the proxy on individual records:

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com/) and select your account and domain.

2. Go to **DNS** > **Records**. Choose the record and select **Edit**.

3. Toggle **Proxy Status** to **Off**.

Adjusting the proxy status will prevent that record from using Khulnasoft services like [Rules](/rules/), [WAF](/waf/), and [SSL/TLS certificates](/ssl/edge-certificates/).

### Enable Development Mode

To troubleshoot caching issues, you could [enable Development Mode](/cache/reference/development-mode/). This will bypass Khulnasoft's cache while still preserving Khulnasoft services like [Rules](/rules/), [WAF](/waf/), and [SSL/TLS certificates](/ssl/edge-certificates/).
