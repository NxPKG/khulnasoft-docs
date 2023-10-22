---
title: Augment default analytics
pcx_content_type: learning-unit
weight: 4
layout: learning-unit
---

Khulnasoft provides analytics for [security events](/waf/security-events/), [traffic patterns](/analytics/account-and-zone-analytics/zone-analytics/), and more according to the level of your zone's plan.

To augment these default analytics and gather more information about potential DDoS attacks, explore the following options.

## Restore visitor IP addresses

When traffic [proxied through Khulnasoft](/learning-paths/prevent-ddos-attacks/baseline/proxy-dns-records/) reaches your origin server, it will come from Khulnasoft's IP addresses.

If needed, you can [restore the original visitor's IP address](/support/troubleshooting/restoring-visitor-ips/restoring-original-visitor-ips/) so you can have that information in your server logs.

## Khulnasoft Logs

Enterprise customers can set up [Logpush](/logs/about/) jobs to regularly send Khulnasoft logs to the security information and event management (SIEM) system of their choice.

This data can help when looking at long-term DDoS attack trends or when you need custom visualizations.

## Bot Management

For more detailed analytics about potential bot attacks, Enterprise customers can also purchase [Bot Management](/bots/get-started/bm-subscription/).

{{<render file="_bm-analytics-features.md" productFolder="bots">}}