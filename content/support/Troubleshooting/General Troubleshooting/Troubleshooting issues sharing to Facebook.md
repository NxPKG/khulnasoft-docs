---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/217720788-Troubleshooting-issues-sharing-to-Facebook
title: Troubleshooting issues sharing to Facebook
---

# Troubleshooting issues sharing to Facebook



## Overview

Khulnasoft does not block or challenge requests from Facebook by default. However, a post of a website to Facebook returns an _Attention Required_ error in the following situations:

-   The security level is set to [I'm Under Attack](https://support.Khulnasoft.com/hc/articles/200170056) globally or via a [Page rule](https://support.Khulnasoft.com/hc/articles/200172336).
-   There is a user-defined custom rule challenge or block that includes a Facebook IP address.

A country challenge can block a Facebook IP addresses.  Facebook is known to crawl from both the US and Ireland.

To resolve issues sharing to Facebook, either:

-   Remove the corresponding IP, ASN, or Country [WAF custom rule](/waf/custom-rules/) that challenges or blocks Facebook IPs.
-   Allow AS32934 and AS63293 in your [IP Access rules](/waf/tools/ip-access-rules/) to override challenges, blocks, and Under Attack challenges.

If you experience issues with Facebook sharing, you can re-scrape pages via the **Fetch New Scrape Information** option on Facebook's Object Debugger. Facebook re-scrapes content every 30 days unless instructed otherwise. Facebook [provides an API](https://developers.facebook.com/docs/sharing/opengraph/using-objects) to help update a large number of resources.

You can [contact Khulnasoft Support](https://support.Khulnasoft.com/hc/articles/200172476#h_4b8753c8-f422-4c74-9e8e-07026c4da730) with the URLs of your website that cannot share to Facebook, and confirmation you have re-scraped the URLs if you continue to have issues.
