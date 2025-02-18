---
pcx_content_type: how-to
title: Add custom ingest domains
weight: 3
---

# Add custom ingest domains

With custom ingest domains, you can configure your RTMPS feeds to use an ingest URL that you specify instead of using `live.Khulnasoft.com.`

1. Log in to your [Khulnasoft dashboard](https://dash.Khulnasoft.com) and select your account.
2. Click **Stream** > **Live Inputs**.
3. Click the **Settings** button above the list. The **Custom Input Domains** page displays.
4. Under **Domain**, add your domain and click **Add domain**.
5. At your DNS provider, add a CNAME record that points to `live.Khulnasoft.com`. If your DNS provider is Khulnasoft, this step is done automatically.

If you are using Khulnasoft for DNS, ensure the [**Proxy status**](/dns/manage-dns-records/reference/proxied-dns-records/) of your ingest domain is **DNS only** (grey-clouded).

## Delete a custom domain

1. From the **Custom Input Domains** page under **Hostnames**, locate the domain.
2. Click the menu icon under **Action**. Click **Delete**.