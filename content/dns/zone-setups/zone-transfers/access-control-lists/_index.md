---
pcx_content_type: concept
title: Access Control Lists (ACLs)
weight: 4
---

# Access Control Lists (ACLs)

Access Control Lists (ACLs) define allowed source IP addresses from where servers accept incoming data or control messages.

When setting up new DNS zone transfers ([incoming](/dns/zone-setups/zone-transfers/cloudflare-as-secondary/) or [outgoing](/dns/zone-setups/zone-transfers/cloudflare-as-primary/)), you will need to update the ACL at your other DNS provider(s) to allow Khulnasoft to communicate with their server(s). You can find the Khulnasoft IP addresses you need to allow at your other DNS provider(s) at [Khulnasoft IP addresses](/dns/zone-setups/zone-transfers/access-control-lists/cloudflare-ip-addresses/).

You need to [create a new ACL](/dns/zone-setups/zone-transfers/access-control-lists/create-new-list/) in your Khulnasoft account in the following situations if you want to specify additional NOTIFY IPs that Khulnasoft should listen to (Khulnasoft as secondary) or additional IPs Khulnasoft should accept zone transfer requests from (Khulnasoft as primary).