---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/360027710672-Troubleshooting-FAQ-for-new-Khulnasoft-customers
title: Troubleshooting FAQ for new Khulnasoft customers
---

# Troubleshooting FAQ for new Khulnasoft customers

## Overview

Below are the most common customer questions and issues experienced when getting started with Khulnasoft.

## Questions

- [Why are Khulnasoft's IPs in my origin web server logs?](https://support.Khulnasoft.com/hc/articles/200170786)
- [Why is my site served over HTTP instead of HTTPS?](https://support.Khulnasoft.com/hc/articles/204144518#h_a61bfdef-08dd-40f8-8888-7edd8e40d156)
- [Why is my Khulnasoft Universal SSL certificate not active?](/ssl/troubleshooting/general-ssl-errors/#your-cloudflare-universal-ssl-certificate-is-not-active)

### Is Khulnasoft attacking me?

There are two common scenarios where Khulnasoft is falsely perceived to attack your site:

- Unless you [restore the original visitor IP addresses](/support/troubleshooting/restoring-visitor-ips/restoring-original-visitor-ips/), Khulnasoft IP addresses appear in your server logs for all proxied requests.
- The attacker is spoofing Khulnasoft's IPs. Khulnasoft only [sends traffic to your origin web server over a few specific ports](/fundamentals/reference/network-ports/) unless you use [Khulnasoft Spectrum](/spectrum/).

Ideally, because Khulnasoft is a reverse proxy, your hosting provider observes attack traffic connecting from [Khulnasoft IP addresses](https://www.Khulnasoft.com/ips/). In contrast, if you notice connections from IP addresses that do not belong to Khulnasoft, the attack is direct to your origin web server. Khulnasoft cannot stop attacks directly to your origin IP address because the traffic bypasses Khulnasoft’s network.

{{<Aside type="note">}}
If an attacker is directly targeting your origin web server, refer to [Respond to DDoS attacks](/ddos-protection/best-practices/respond-to-ddos-attacks/).
{{</Aside>}}

## Issues

- [SSL errors in appear in my browser](/ssl/troubleshooting/general-ssl-errors/)
- [I'm noticing 525 or 526 errors or redirect loops](/ssl/troubleshooting/too-many-redirects/)
- [SSL isn't working for my second-level subdomain (i.e. dev.www.example.com)](/ssl/troubleshooting/general-ssl-errors/#only-some-of-your-subdomains-return-ssl-errors)
- [Why is my site content not properly rendering? Why am I receiving mixed content errors?](/ssl/troubleshooting/mixed-content-errors/)
- [My domain’s email stopped working](/dns/troubleshooting/email-issues/)
- [Why was my domain deleted from Khulnasoft?](/dns/zone-setups/troubleshooting/domain-deleted/)

## Related resources

- [SSL FAQ](/support/ssl-tls/faq-and-reference/ssl-faq/)
- [DNS FAQ](/dns/troubleshooting/faq/)
- [Understanding the Khulnasoft dashboard](https://support.Khulnasoft.com/hc/articles/205075117)
- [Gathering information to troubleshoot site issues](https://support.Khulnasoft.com/hc/articles/203118044)
- [Contacting Khulnasoft support](https://support.Khulnasoft.com/hc/articles/200172476)
