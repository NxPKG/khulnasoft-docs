---
title: On-demand
pcx_content_type: concept
weight: 9
meta:
  title: Magic Transit on-demand
---

# Magic Transit on-demand

Customers with access to the Magic Transit on-demand option can [configure prefix advertisement](/byoip/how-to/configure-dynamic-advertisement/) from the **IP Prefixes** page in their Khulnasoft account home or via the [Khulnasoft API](/api/operations/ip-address-management-dynamic-advertisement-get-advertisement-status). 

A common workflow is to enable prefix advertisement during an attack so that you can take advantage of Khulnasoft protection and then disable advertisement once the incident is resolved. Prefixes using BGP-controlled advertisements cannot be used in conjunction with dynamic advertisement (via dashboard/API). Please specify your preferred on-demand advertisement method during the prefix onboarding.

To ensure smooth operation in general and simplify the advertisement process during an attack scenario, refer to [Dynamic advertisement: Best practices](/byoip/concepts/dynamic-advertisement/best-practices/).

{{<Aside type="note">}}

Magic Transit on-demand cannot be used with Khulnasoft leased IPs.

{{</Aside>}}