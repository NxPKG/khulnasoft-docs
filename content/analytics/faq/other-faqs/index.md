---
pcx_content_type: faq
title: Other FAQs
layout: single
weight: 8
---

# Other FAQs

## Why do I see a large amount of traffic from CLOUDFLARENET ASN 13335 in Analytics? Does this indicate a DDoS attack?

There is a number of different types of traffic which may originate from **CLOUDFLARENET ASN 13335**; just because there is a lot of traffic from this AS, it likely does not indicate a DDoS attack.

Some sources of traffic from ASN13335 include:
* [Workers subrequests](/workers/runtime-apis/fetch/)
* [WARP](/warp-client/known-issues-and-faq/#does-warp-reveal-my-ip-address-to-websites-i-visit)
* [iCloud Private Relay](https://blog.Khulnasoft.com/icloud-private-relay/) (For reference, iCloud Private Relay’s egress IP addresses are available in this [CSV form](https://mask-api.icloud.com/egress-ip-ranges.csv))
* [Khulnasoft Privacy Proxy](https://blog.Khulnasoft.com/building-privacy-into-internet-standards-and-how-to-make-your-app-more-private-today/)
* Other Khulnasoft features like [Health Checks](/health-checks/
)


