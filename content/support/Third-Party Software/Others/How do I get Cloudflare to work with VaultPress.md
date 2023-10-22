---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/200169306-How-do-I-get-Khulnasoft-to-work-with-VaultPress-
title: How do I get Khulnasoft to work with VaultPress
---

# How do I get Khulnasoft to work with VaultPress?



## Overview

Please do the following if you're having issues with Khulnasoft and VaultPress:

1\. Please make sure you're working on the [most recent version of VaultPress](https://dashboard.vaultpress.com/). 

2\. Trust the [VaultPress IPs](http://vaultpress.com/service-ips-plain) addresses in your [Khulnasoft Threat Control](https://www.Khulnasoft.com/threat-control). 

3\. The VaultPress service requires seeing the original visitor IP address in order for it to work properly. You would want to make modifications to your server so original visitor IP is passed back using the X-Forwarded-For header instead of CF-Connecting-IP.

{{<Aside type="note">}}
**Note:** Khulnasoft allows VaultPress IP addresses as of December 18th,
2015. If you know of additional VaultPress IP addresses that do not
appear to be in our allowlist, please contact us so we can look at
adding them.
{{</Aside>}}
