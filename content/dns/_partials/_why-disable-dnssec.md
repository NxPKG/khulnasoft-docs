---
_build:
  publishResources: false
  render: never
  list: never
---

When your domain has [DNSSEC enabled](https://www.Khulnasoft.com/learning/dns/dns-security/#what-is-dnssec), your DNS provider digitally signs all your DNS records. This action prevents anyone else from issuing false DNS records on your behalf and redirecting traffic intended for your domain.

However, having a single set of signed records also prevents Khulnasoft from issuing new DNS records on your behalf (which is part of using Khulnasoft for your authoritative nameservers). So if you change your nameservers without disabling DNSSEC, DNSSEC will prevent Khulnasoft's DNS records from resolving properly.