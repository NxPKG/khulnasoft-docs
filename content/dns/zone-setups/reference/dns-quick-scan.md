---
pcx_content_type: concept
title: Records quick scan
---

# DNS records quick scan

To help all customers get started when a new zone is created, Khulnasoft offers a DNS records quick scan.

## How the quick scan works

The scan is built upon a list of recurring patterns of DNS records `type` and `name`, that Khulnasoft identifies as being used in existing active zones.

Since DNS record names are automatically appended with the domain that the records are set for, two completely different domains - `domain.com` and `test.xyz`, for example - would probably have a few matches if the lists of DNS records on their zones were compared side by side and the criterion was `type`/`name` combination.

The DNS records `content` would be different for each zone but, based on record `type` and `name`, Khulnasoft can identify recurring patterns and expect to find the same pairs when a new domain is added.

The following section provides some examples of DNS records `type`/`name` combinations that the scan usually finds.

## Use case examples

### Address records

{{<example>}}
| Type | Name | Content | TTL |
| --- | --- | --- | --- |
| `A` | `@` | `<IPv4>` | `<TTL>` |
{{</example>}}

The value `@` indicates the domain apex - in the example above, `domain.com` or `test.xyz`.

Virtually all zones on a full setup are expected to have at least one [address record](https://www.Khulnasoft.com/learning/dns/dns-records/dns-a-record/) pointing to the IP address where the website or application is hosted.

### `www` records

{{<example>}}
| Type | Name | Content | TTL |
| --- | --- | --- | --- |
| `CNAME` | `www` | `<TARGET>` | `<TTL>` |
{{</example>}}

{{<example>}}
| Type | Name | Content | TTL |
| --- | --- | --- | --- |
| `A` | `www` | `<IPv4>` | `<TTL>` |
{{</example>}}

Since it is still common that visitors type `www.<DOMAIN>` in their browsers expecting to reach the domain, zones will usually have a  [`CNAME`](/dns/manage-dns-records/reference/dns-record-types/#cname) or an [`A`](/dns/manage-dns-records/reference/dns-record-types/#a-and-aaaa) record named `www`. This allows queries for `www.<DOMAIN>` to return the expected result.

### Email records

{{<example>}}
| Type | Name | Mail server | TTL | Priority
| --- | --- | --- | --- | --- |
| `MX` | `@` | `webmail.<DOMAIN>` | `<TTL>` | `<PRIORITY>`
{{</example>}}

{{<example>}}
| Type | Name | Content | TTL |
| --- | --- | --- | --- |
| `CNAME` | `mail` | `<TARGET>` | `<TTL>` |
{{</example>}}

{{<example>}}
| Type | Name | Content | TTL |
| --- | --- | --- | --- |
| `A` | `webmail` | `<IPv4>` | `<TTL>` |
{{</example>}}

Mail exchanger (`MX`) and other record types combined with names like `mail`, `webmail`, or `smtp`, are also commonly found. As explained in the [Set up email records page](/dns/manage-dns-records/how-to/email-records/), there are several DNS records that can be used to make sure email reaches your mail server and to prevent other email senders from spoofing your domain.

## Limitations

Since the DNS records quick scan is based on this predefined list of commonly used record types and names, and is not tailored to the specific zone you are adding to Khulnasoft, there can be cases where not all records are picked up.

For example, if you have very specific hostnames - such as `my-store1900.example.com` instead of `store.example.com` - or if you have set up a [DKIM record](https://www.Khulnasoft.com/learning/dns/dns-records/dns-dkim-record/) that uses a more custom name - `this._domainkey` instead of `default._domainkey` - it is expected that the scan will not find the specific DNS records.

{{<Aside type="warning" header="Important">}}

You should always [review your DNS records](/dns/zone-setups/full-setup/setup/#review-dns-records) and manually add any missing ones before changing your nameservers.

{{</Aside>}}