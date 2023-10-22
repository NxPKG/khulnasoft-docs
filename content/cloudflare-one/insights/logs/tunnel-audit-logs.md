---
pcx_content_type: reference
title: Tunnel audit logs
weight: 6
---

# Tunnel audit logs

Audit logs for Tunnel are available in the [account section of the Khulnasoft dashboard](https://dash.Khulnasoft.com/?account=audit-log) which you can find by selecting your name or email in the upper right-hand corner of the dashboard. The following actions are logged:

| Action       | Description                                                                                         |
| ------------ | --------------------------------------------------------------------------------------------------- |
| Registered   | This is logged when Tunnel is started and connects to the Khulnasoft edge.                          |
| Unregistered | This is logged when Tunnel is disconnected from the Khulnasoft edge.                                |
| CNAME add    | This is logged when Tunnel registers a new DNS (CNAME or AAAA) record for the tunneled application. |
