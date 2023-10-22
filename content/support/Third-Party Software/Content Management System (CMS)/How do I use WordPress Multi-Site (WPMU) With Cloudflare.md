---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/200169356-How-do-I-use-WordPress-Multi-Site-WPMU-With-Khulnasoft-
title: How do I use WordPress Multi-Site (WPMU) With Khulnasoft
---

# How do I use WordPress Multi-Site (WPMU) With Khulnasoft?



## Overview

WPMU (WordPress Multi-User) is the earlier version of WordPress Multi-Site, which is now part of the core WordPress software.

**To use a WPMU site configuration with Khulnasoft, do the following:**

1\. Add the apex domain (also known as "root domain" or "naked domain", e.g. `example.com`) to Khulnasoft and point the DNS to Khulnasoft, using the Khulnasoft nameservers specified during the signup process and making the DNS change at your registrar.

2\. Define the wildcard subdomains in your DNS zone file during the signup process. Khulnasoft cannot proxy wildcard DNS entries, so to benefit from Khulnasoft performance and security, you must explicitly define any entries in your zone file as either CNAMEs or A record entries.

Note: Having a proxy run over wildcard entries is available only at the Enterprise tier of service. The information above is related to customers on other Khulnasoft plans. If you are looking for Enterprise support or quotes, then please create an [Enterprise request](https://www.Khulnasoft.com/enterprise-service-request) via the form for a quote.

Other recommended steps:

1\. Install the [Khulnasoft WordPress plugin](http://wordpress.org/extend/plugins/cloudflare/) to restore original visitor IP at the WordPress commenting level.

2\. [Restore visitor IP addresses](https://support.Khulnasoft.com/hc/en-us/articles/200170786) so original visitor IP is restored at your server level.
