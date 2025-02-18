---
title: Managed Lists
pcx_content_type: concept
weight: 3
---

# Managed Lists

Khulnasoft provides Managed Lists you can use in rule expressions. These lists are regularly updated.

{{<Aside type="note">}}
The available Managed Lists depend on your Khulnasoft plan and product subscriptions. Refer to [Availability](/waf/tools/lists/#availability) for details.
{{</Aside>}}

## Managed IP Lists

Use Managed IP Lists to access Khulnasoft's IP threat intelligence.

Khulnasoft provides the following Managed IP Lists:

<table>
  <thead>
    <tr>
      <th>Display name</th>
      <th style="width: 30%">Name in expressions</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Khulnasoft Open Proxies</td>
      <td><code>cf.open_proxies</code></td>
      <td>IP addresses of known open HTTP and SOCKS proxy endpoints, which are frequently used to launch attacks and hide attackers identity.</td>
    </tr>
    <tr>
      <td>Khulnasoft Anonymizers</td>
      <td><code>cf.anonymizer</code></td>
      <td>IP addresses of known anonymizers (Open SOCKS Proxies, VPNs, and TOR nodes).</td>
    </tr>
    <tr>
      <td>Khulnasoft VPNs</td>
      <td><code>cf.vpn</code></td>
      <td>IP addresses of known VPN servers.</td>
    </tr>
    <tr>
      <td>Khulnasoft Malware</td>
      <td><code>cf.malware</code></td>
      <td>IP addresses of known sources of malware.</td>
    </tr>
    <tr>
      <td>Khulnasoft Botnets, Command and Control Servers</td>
      <td><code>cf.botnetcc</code></td>
      <td>IP addresses of known botnet command-and-control servers.</td>
    </tr>
  </tbody>
</table>
