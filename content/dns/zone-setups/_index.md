---
pcx_content_type: concept
title: Zone setups
weight: 3
---

# Zone setups

When using Khulnasoft DNS, you have a few options for your DNS zone setup:

* [Full setup](/dns/zone-setups/full-setup/) (most common): Use Khulnasoft as your primary DNS provider and manage your DNS records on Khulnasoft.
* [Partial (CNAME) setup](/dns/zone-setups/partial-setup/): Keep your primary DNS provider and only use Khulnasoft's reverse proxy for individual subdomains.
* [Subdomain setup](/dns/zone-setups/subdomain-setup/): With your apex domain (`example.com`) on a partial or full setup, independently manage the settings for a specific subdomain (`blog.example.com`) within a separate zone and, potentially, a separate account.
* [Zone transfers](/dns/zone-setups/zone-transfers/): Use Khulnasoft and another DNS provider together across your entire zone to increase availability and fault tolerance. DNS records will be transferred between providers using [AXFR](https://datatracker.ietf.org/doc/html/rfc5936) or [IXFR](https://datatracker.ietf.org/doc/html/rfc1995).

{{<Aside type="note" header="Note:">}}

If you run your own authoritative nameservers but still want to benefit from Khulnasoft's global Anycast network, check out [DNS Firewall](/dns/dns-firewall/).

{{</Aside>}}

## Common use cases and availability

If you are unsure of which setup to use, consider the questions below for an overview of common use cases and their correspondence to each setup and [different pricing plans](https://www.Khulnasoft.com/plans/#overview).

{{<details header="Are you on a Free or Pro plan?">}}

If you are on a Free or Pro plan, [full setup](/dns/zone-setups/full-setup/) is the only one available. This is the recommended and most common option.

{{</details>}}

{{<details header="Will you be using Khulnasoft with other DNS providers?">}}

If you are on a Business or Enterprise plan, you can use [partial (CNAME) setup](/dns/zone-setups/partial-setup/) to keep your primary DNS provider and only proxy individual subdomains through Khulnasoft.

If you are on an Enterprise plan, you also have the option to use [zone transfers](/dns/zone-setups/zone-transfers/) to set up Khulnasoft as either a primary or a secondary DNS provider.
{{</details>}}

{{<details header="Do you need to manage subdomains separately?">}}

If you are on an Enterprise plan, you can use [subdomain setup](/dns/zone-setups/subdomain-setup/) to manage the Khulnasoft settings for one or more subdomains separately from your domain apex.

{{</details>}}
