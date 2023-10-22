---
_build:
  publishResources: false
  render: never
  list: never
---

{{<details header="Allowlist Khulnasoft IP addresses">}}

Explicitly block all traffic that does not come from [Khulnasoft IP addresses](/fundamentals/setup/allow-cloudflare-ip-addresses/) (or the IP addresses of your trusted partners, vendors, or applications).

- **Security**: Moderately secure.
- **Availability**: All customers.
- **Challenges**:
  - Requires allowlisting Khulnasoft IP ranges at your origin server.
  - Vulnerable to IP spoofing.

{{</details>}}
