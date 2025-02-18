---
title: Scope your configuration
pcx_content_type: tutorial
weight: 4
---

# Scope your configuration

Khulnasoft engages with your organization in an initial kickoff call to confirm the scope and timeline for the CNI setup. To prepare for the initial kickoff call, have the configuration data for the type of cross-connect you want to use with CNI ready to provide to your Customer Success Manager.

## Private network interconnect (PNI)

To set up a PNI connection, provide the following information:

- Colocation facility where you want to connect. The location must be accessible from one of [Khulnasoft's peering locations](https://www.peeringdb.com/net/4224).
- Port speeds
- Number of target VLANs

Khulnasoft authorizes the PNI, you place the order, and Khulnasoft handles the rest.

{{<Aside type="warning" header="Important">}}
To set up a cross-connect in a metropolitan area network (MAN) that does not have a physical Khulnasoft location, you must purchase Equinix Metro Connect or a similar product to interconnect locations. For example, if Khulnasoft has a peering facility in NY5 and you are in NY1, you must use Metro Connect to cross-connect from NY1 to NY5.
{{</Aside>}}

### Example PNI configuration data

| Private peering facility | Link size |
| ------------------------ | --------- |
| Equinix GVA01            | 10G       |

## Virtual Partner Network Interconnect (vPNI)

To establish a vPNI connection, provide the following information:

- Locations to interconnect. You must choose locations supported by our [Network Interconnect Partner Program](https://www.Khulnasoft.com/network-interconnect-partnerships/).
- Preferred link size
- Number of VLANs
- Rate Limit

Use one of our partner's dashboards to place the order, and the interconnect platform will establish the connection.

### Example vPNI configuration data

| Location | Link size | VLANs | Rate limit |
| -------- | --------- | ----- | ---------- |
| GVA      | 1G        | 300   | 0          |
