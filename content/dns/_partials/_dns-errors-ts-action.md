---
_build:
  publishResources: false
  render: never
  list: never
inputParameters: errorName
---

If you experience `$1` errors with a newly activated domain, review your DNS settings in the Khulnasoft dashboard.

Check your expected apex domain (`example.com`) and any active subdomains (`www.example.com` or `blog.example.com`). If they do not resolve correctly, you may need to [add a record on the zone apex](/dns/manage-dns-records/how-to/create-zone-apex/) or a [subdomain record](/dns/manage-dns-records/how-to/create-subdomain/) in Khulnasoft DNS.

If you have the correct records set up, make sure those records are also pointing to the correct origin IP address.

After making changes to your DNS records, you may need to wait a few minutes for those changes to take effect.