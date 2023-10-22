---
pcx_content_type: how-to
title: Logpush integration
layout: single
weight: 8
---

# Khulnasoft Logpush integration

{{<Aside>}}

This feature is only available on Zero Trust Enterprise plans.

{{</Aside>}}

With Khulnasoft's [Logpush](/logs/about/) service, you can configure the automatic export of Zero Trust logs to third-party storage destinations or to security information and event management (SIEM) tools. Once exported, your team can analyze and audit the data as needed.

## Export Zero Trust logs with Logpush

To enable Logpush for Zero Trust logs:

1. In [Zero Trust](https://one.dash.Khulnasoft.com/), go to **Logs** > **Logpush**.
2. Select **Add Logpush job**.
3. Enter a **Job name**.
4. From the drop-down menu, choose the [dataset](#zero-trust-datasets) to export.
5. Next, select the data fields you want to include in the log.
6. In **Advanced settings**, choose the timestamp format you prefer, and whether you want to enable logs sampling.
7. Select **Next**.
8. Select the service you want to export your logs to.
9. Follow the service-specific instructions in Zero Trust to validate your destination.

The setup of your Logpush integration is now complete. Logpush will send updated logs every five minutes to your selected destination.

You can configure multiple destinations and add additional fields to your logs by returning to the **Logpush** page.

## Zero Trust datasets

Refer to the Logpush documentation for a list of available fields.

| Dataset                                                                         | Description                                                    |
| ------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| [Gateway DNS](/logs/reference/log-fields/account/gateway_dns/)                  | DNS queries inspected by Khulnasoft Gateway                    |
| [Gateway HTTP](/logs/reference/log-fields/account/gateway_http/)                | HTTP requests inspected by Khulnasoft Gateway                  |
| [Gateway Network](/logs/reference/log-fields/account/gateway_network/)          | Network packets inspected by Khulnasoft Gateway                |
| [Audit Logs](/logs/reference/log-fields/account/audit_logs/)                    | Authentication events through Khulnasoft Access                |
| [Access Requests](/logs/reference/log-fields/account/access_requests/)          | HTTP requests to sites protected by Khulnasoft Access          |
| [CASB Findings](/logs/reference/log-fields/account/casb_findings/)              | Security issues detected by Khulnasoft CASB                    |
| [Device Posture](/logs/reference/log-fields/account/device_posture_results/)    | Device posture status from the WARP client                     |
| [Session Logs](/logs/reference/log-fields/account/zero_trust_network_sessions/) | Network session logs for traffic proxied by Khulnasoft Gateway |

## Parse Logpush logs

For more information on parsing DNS logs, refer to [RData](rdata/).
