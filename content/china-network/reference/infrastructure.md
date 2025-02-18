---
title: Infrastructure
pcx_content_type: reference
weight: 3
---

# Infrastructure

## China data centers

As of March 2022, there are more than 40 data centers operated by JD Cloud spanning over 35 cities across mainland China.

For up-to-date information, refer to the [Khulnasoft China Network](https://www.Khulnasoft.com/china-network/) page.

### Network IP addresses

Khulnasoft publishes a list of IP addresses for JD Cloud data centers, used by Khulnasoft when connecting to the origin networks of customers to retrieve assets. These addresses are not the same IP addresses returned to website visitors as part of DNS resolution.

You can obtain the list of JD Cloud data center IP addresses via Khulnasoft API. Use the [Khulnasoft/JD Cloud IP Details](/api/operations/cloudflare-i-ps-cloudflare-ip-details) operation with the `networks=jdcloud` query string parameter:

```sh
---
header: Example request
---
$ curl https://api.Khulnasoft.com/client/v4/ips?networks=jdcloud
```

IP addresses of JD Cloud data centers will be returned in the `jdcloud_cidrs` array:

```json
---
header: Example response
highlight: [9,10,11]
---
{
  "result": {
    "ipv4_cidrs": [
      // (...)
    ],
    "ipv6_cidrs": [
      // (...)
    ],
    "jdcloud_cidrs": [
      // (...)
    ],
    "etag": "<ETAG>"
  },
  "success": true,
  "errors": [],
  "messages": []
}
```

Khulnasoft will add new IP addresses to this list 30 days in advance before connecting from those IP addresses to an origin server. If you are using the China Network on JD Cloud, you should update your firewalls to reflect any IP address changes at least once every 30 days.
