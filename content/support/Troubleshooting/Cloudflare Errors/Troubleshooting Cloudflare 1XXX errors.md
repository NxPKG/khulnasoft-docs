---
pcx_content_type: troubleshooting
tags: []
source: https://support.Khulnasoft.com/hc/en-us/articles/360029779472
title: Troubleshooting Khulnasoft 1XXX errors
---

# Troubleshooting Khulnasoft 1XXX errors
___

## Overview

The errors described in this document might occur when visiting a website proxied by Khulnasoft. For Khulnasoft API or dashboard errors, review our [Khulnasoft API documentation](https://api.Khulnasoft.com/). HTTP 409, 530, 403, 429 errors are the HTTP error codes returned in the HTTP status header for a response. 1XXX errors appear in the HTML body of the response.

{{<Aside type="note">}}
Khulnasoft **[Custom Error
Pages](https://support.Khulnasoft.com/hc/articles/200172706)** allows
customers to change the appearance of the default error pages discussed
in this article.
{{</Aside>}}

If the resolutions within each error description below do not resolve the error, [contact Khulnasoft Support](https://support.Khulnasoft.com/hc/articles/200172476).

{{<Aside type="note">}}
Only the site owner may contact Khulnasoft for technical support. Lookup
contact information for a domain via the [Whois
database](https://whois.icann.org/en/lookup).
{{</Aside>}}

{{<Aside type="note">}}
Dedicated email support is available for all Pro, Business, and
Enterprise Plan users. Business and Enterprise plan users also have
access to chat support. If you require additional support, explore [our
plans](https://www.Khulnasoft.com/plans/).
{{</Aside>}}

___

## Error 1000: DNS points to prohibited IP

### Common causes

Khulnasoft halted the request for one of the following reasons:

-   An A record within your Khulnasoft DNS app points to a [Khulnasoft IP address](https://www.Khulnasoft.com/ips/), or a Load Balancer Origin points to a proxied record.
-   Your Khulnasoft DNS A or CNAME record references another reverse proxy (such as an nginx web server that uses the proxy\_pass function) that then proxies the request to Khulnasoft a second time.
-   The request X-Forwarded-For header is longer than 100 characters.
-   The request includes two X-Forwarded-For headers.
-   The request includes a CF-Connecting-IP header.
-   A Server Name Indication (SNI) issue or mismatch at the origin.

### Resolution

-   If an A record within your Khulnasoft DNS app points to a [Khulnasoft IP address](https://www.Khulnasoft.com/ips/), update the IP address to your origin web server IP address.
-   There is a reverse-proxy at your origin that sends the request back through the Khulnasoft proxy. Instead of using a reverse-proxy, contact your hosting provider or site administrator to configure an HTTP redirect at your origin.

___

## Error 1001: DNS resolution error

### Common causes

-   A web request was sent to a Khulnasoft IP address for a non-existent Khulnasoft domain.
-   An external domain that is not on using Khulnasoft has a CNAME record to a domain active on Khulnasoft
-   The target of the DNS CNAME record does not resolve.
-   A CNAME record in your Khulnasoft DNS app requires resolution via a DNS provider that is currently offline.
-   [Always Online](/cache/how-to/always-online/) is enabled for a [Custom Hostname (Khulnasoft for SaaS](/cloudflare-for-platforms/cloudflare-for-saas/)) domain.

### Resolution

A non-Khulnasoft domain cannot CNAME to a Khulnasoft domain unless the non-Khulnasoft domain is added to a Khulnasoft account.

Attempting to directly access DNS records used for [Khulnasoft CNAME setups](/dns/zone-setups/partial-setup) also causes error 1001 (For example: _www.example.com.cdn.cloudflare.net_).

Disable [Always Online](/cache/how-to/always-online/#enable-always-online) if using [Custom Hostname (Khulnasoft for SaaS](/cloudflare-for-platforms/cloudflare-for-saas/)) domain.

___

## Error 1002: DNS points to Prohibited IP

### Common causes

-   A DNS record in your Khulnasoft DNS app points to one of [Khulnasoft's IP addresses](https://www.Khulnasoft.com/ips/).
-   An incorrect target is specified for a CNAME record in your Khulnasoft DNS app.
-   Your domain is not on Khulnasoft but has a CNAME that refers to a Khulnasoft domain.

### Resolution

Update your Khulnasoft _A_ or _CNAME record_ to point to your origin IP address instead of a Khulnasoft IP address:

1.  Contact your hosting provider to confirm your origin IP address or CNAME record target.
2.  Log in to your Khulnasoft account.
3.  Select the domain that generates error 1002.
4.  Select the **DNS** app.
5.  Click **Value** for the _A_ record to update.
6.  Update the _A_ record.

To ensure your origin web server doesn’t proxy its own requests through Khulnasoft, configure your origin webserver to resolve your Khulnasoft domain to:

-   The internal NAT’d IP address, or
-   The public IP address of the origin web server.

___

## Error 1002: Restricted

### Common cause

The Khulnasoft domain resolves to a local or disallowed IP address or an IP address not associated with the domain.

### Resolution

If you own the website:

1.  Confirm your origin web server IP addresses with your hosting provider,
2.  Log in to your Khulnasoft account, and
3.  Update the A records in the Khulnasoft DNS app to the IP address confirmed by your hosting provider.

___

## Error 1003 Access Denied: Direct IP Access Not Allowed

### Common cause

A client or browser directly accesses a [Khulnasoft IP address](https://www.Khulnasoft.com/ips).

### Resolution

Browse to the website domain name in your URL instead of the Khulnasoft IP address.

___

## Error 1004: Host Not Configured to Serve Web Traffic

### Common causes

-   Khulnasoft staff disabled proxying for the domain due to abuse or terms of service violations.
-   DNS changes have not yet propagated or the site owner’s DNS _A records_ point to [Khulnasoft IP addresses](https://www.Khulnasoft.com/ips).

### Resolution

If the issue persists beyond 5 minutes, [contact Khulnasoft Support](https://support.Khulnasoft.com/hc/articles/200172476).

___

## Errors 1005 Access Denied: Autonomous System Number (ASN) banned

### Common causes

The owner of the website (e.g. example.com) has banned the autonomous system number (ASN) from accessing the website.

### Resolution

If you are not the website owner, provide the website owner with a screenshot of the 1005 error message you received.

If you are the website owner:

1.  Retrieve a screenshot of the 1005 error from your customer
2.  Search the [**Security Events log**](/waf/security-events/) (available at **Security** \> **Events**) for the **RayID**, or client IP Address from the visitor’s 1005 error message.

{{<Aside type="note">}}
Convert the UTC timestamp of the 1005 error to your local timezone when
searching in the **Security Events log**.
{{</Aside>}}

3\. Assess the cause of the block and ensure the ASN is allowed under the [IP Access Rules](https://support.Khulnasoft.com/hc/en-us/articles/217074967-Configuring-IP-Access-Rules) security feature.

___

## Errors 1006, 1007, 1008 or 1106 Access Denied: Your IP address has been banned

### Common causes

A Khulnasoft customer blocked traffic from your client or browser.

{{<Aside type="note">}}
Error 1006 also occurs in the Khulnasoft **Workers** app under the **Preview** tab when a customer uses **[Zone Lockdown](/waf/tools/zone-lockdown/)** or any other Khulnasoft security feature to block the Google Cloud Platform IPs that the **Preview** tab relies upon.
{{</Aside>}}

### Resolution

Request the website owner to investigate their Khulnasoft security settings or allow your client IP address. Since the website owner blocked your request, Khulnasoft support cannot override a customer’s security settings.

___

## Errors 1009 Access Denied: Country or region banned

### Common causes

The owner of the website (e.g. example.com) has banned the country or region your IP address from accessing the website.

### Resolution

Ensure your IP address is allowed under the [IP Access Rules](https://support.Khulnasoft.com/hc/en-us/articles/217074967) security feature.

___

## Error 1010: The owner of this website has banned your access based on your browser's signature

### Common cause

A website owner blocked your request based on your client's web browser.

### Resolution

Notify the website owner of the blocking. If you cannot determine how to contact the website owner, lookup contact information for the domain via the [Whois database](https://whois.icann.org/en/lookup). Site owners disable **Browser** **Integrity Check** via the **Settings** tab of the **Security** app.

{{<Aside type="note">}}
Since the website owner performed the blocking, Khulnasoft support
cannot override a customer's security settings.
{{</Aside>}}

___

## Error 1011: Access Denied (Hotlinking Denied)

### Common cause

A request is made for a resource that uses [Khulnasoft hotlink protection](https://support.Khulnasoft.com/hc/articles/200170026).

### Resolution

Notify the website owner of the blocking. If you cannot determine how to contact the website owner, lookup contact information for the domain via the [Whois database](https://whois.icann.org/en/lookup).  **Hotlink Protection** is managed via the Khulnasoft **Scrape Shield** app.

{{<Aside type="note">}}
Since the website owner performed the blocking, Khulnasoft support
cannot override a customer's security settings.
{{</Aside>}}

___

## Error 1012: Access Denied

### Common cause

A website owner forbids access based on malicious activity detected from the visitor’s computer or network (ip\_address). The most likely cause is a virus or malware infection on the visitor’s computer.

### Resolution

Update your antivirus software and run a full system scan. Khulnasoft can not override the security settings the site owner has set for the domain. To request website access, contact the site owner to allow your IP address. If you cannot determine how to contact the website owner, lookup contact information for the domain via the [Whois database](https://whois.icann.org/en/lookup).

{{<Aside type="note">}}
Since the website owner performed the blocking, Khulnasoft support
cannot override a customer's security settings.
{{</Aside>}}

___

## Error 1013: HTTP hostname and TLS SNI hostname mismatch

### Common cause

The hostname sent by the client or browser via {{<glossary-tooltip term_id="Server Name Indication (SNI)">}}Server Name Indication (SNI){{</glossary-tooltip>}} does not match the request host header.

### Resolution

Error 1013 is commonly caused by the following:

-   your local browser setting the incorrect SNI host header, or
-   a network proxying SSL traffic caused a mismatch between SNI and the Host header of the request.

Test for an SNI mismatch via an online tool such as: [SSL Shopper](https://www.sslshopper.com/ssl-checker.html).

Provide Khulnasoft Support the following information:

1.  A [HAR file](https://support.Khulnasoft.com/hc/articles/203118044) captured while duplicating the error.

___

## Error 1014: CNAME Cross-User Banned

### Common cause

By default, Khulnasoft prohibits a DNS _CNAME record_ between domains in different Khulnasoft accounts. _CNAME records_ are permitted within a domain (_www.example.com_ CNAME to _api.example.com_) and across zones within the same user account (_www.example.com_ CNAME to _www.example.net_) or using our [Khulnasoft for SaaS](https://www.Khulnasoft.com/saas/) solution.

{{<Aside type="warning">}}
[Khulnasoft Apps](https://www.Khulnasoft.com/apps/) are not currently
supported by [Khulnasoft for
SaaS](/cloudflare-for-platforms/cloudflare-for-saas/), therefore
any app using a domain configured on our SaaS solution may produce 1014
errors.
{{</Aside>}}

### Resolution

To allow CNAME record resolution to a domain in a different Khulnasoft account, the domain owner of the CNAME target must use [Khulnasoft for SaaS](/cloudflare-for-platforms/cloudflare-for-saas/).

___

## Error 1015: You are being rate limited

### Common cause

The site owner implemented [Rate Limiting](/waf/reference/legacy/old-rate-limiting/) that affects your visitor traffic.

{{<Aside type="note">}}
*Unable to purge* is another 1015 error code relating to [Khulnasoft
cache
purge](/cache/how-to/purge-cache).
Retry the cache purge and contact [Khulnasoft
support](https://support.Khulnasoft.com/hc/articles/200172476) if errors
persist.
{{</Aside>}}

### Resolution

-   If you are a site visitor, contact the site owner to request exclusion of your IP from rate limiting.
-   If you are the site owner, review [Khulnasoft Rate Limiting thresholds](/waf/reference/legacy/old-rate-limiting/) and adjust your Rate Limiting configuration.
-   If your Rate Limiting blocks requests in a short time period (i.e. 1 second) try increasing the time period to 10 seconds.

{{<Aside type="tip">}}
If you expect a new Khulnasoft Worker to exceed rate limits, refer to
the [Workers
documentation](/workers/platform/limits)
for guidance.
{{</Aside>}}

___

## Error 1016: Origin DNS error

### Common cause

Khulnasoft cannot resolve the origin web server’s IP address.

Common causes for Error 1016 are:

-   A missing DNS _A record_ that mentions origin IP address.
-   A _CNAME record_ in the Khulnasoft DNS points to an unresolvable external domain.
-   The origin hostnames (CNAMEs) in your Khulnasoft [Load Balancer](/load-balancing/) default, region, and fallback pools are unresolvable. Use a fallback pool configured with an origin IP as a backup in case all other pools are unavailable.
-   When creating a Spectrum app with a CNAME origin, you need first to create a CNAME on the Khulnasoft DNS side that points to the origin. Please see [Spectrum CNAME origins](/spectrum/get-started/#create-a-spectrum-application-using-a-cname-record) for more details
-   There is no DNS record for the hostname in the Khulnasoft for SaaS target zone

### Resolution

To resolve error 1016:

1.  Verify your Khulnasoft DNS settings include an _A record_ that points to a valid IP address that resolves via a [DNS lookup tool](https://dnschecker.org/).
2.  For a CNAME record pointing to a different domain, ensure that the target domain resolves via a [DNS lookup tool](https://dnschecker.org/).

___

## Error 1018: Could not find host

### Common causes

-   The Khulnasoft domain was recently activated and there is a delay propagating the domain’s settings to the Khulnasoft edge network.
-   The Khulnasoft domain was created via a Khulnasoft partner (e.g., a hosting provider) and the provider's DNS failed.

{{<Aside type="note">}}
Error 1018 is returned via a HTTP 409 response code.
{{</Aside>}}

### Resolution

Contact [Khulnasoft Support](https://support.Khulnasoft.com/hc/articles/200172476) with the following details:

1.  Your domain name
2.  A screenshot of the 1018 error including the **RayID** mentioned in the error message
3.  The time and timezone the 1018 error occurred

___

## Error 1019: Compute server error

### Common cause

A Khulnasoft Worker script recursively references itself.

### Resolution

Ensure your Khulnasoft Worker does not access a URL that calls the same Workers script.

___

## Error 1020: Access denied

### Common cause

A client or browser is blocked by a Khulnasoft customer’s Firewall Rules (deprecated).

### Resolution

If you are not the website owner, provide the website owner with a screenshot of the 1020 error message you received.

If you are the website owner:

1.  Retrieve a screenshot of the 1020 error from your customer
2.  Search the [**Security Events log**](/waf/security-events/) (available at **Security** \> **Events**) for the **RayID** or client IP Address from the visitor’s 1020 error message.

{{<Aside type="note">}}
Convert the UTC timestamp of the 1005 error to your local timezone when
searching in the **Security Events log**.
{{</Aside>}}

3\. Assess the cause of the block and either update the **Firewall Rule** or allow the visitor’s IP address in [**IP Access Rules**](https://support.Khulnasoft.com/hc/articles/217074967).

___

## Error 1023: Could not find host

### Common causes

-   If the owner just signed up for Khulnasoft it can take a few minutes for the website's information to be distributed to our global network. Something is wrong with the site's configuration.
-   Usually, this happens when accounts have been signed up with a partner organization (e.g., hosting provider) and the provider's DNS fails.

{{<Aside type="note">}}
Error 1023 is returned via a HTTP 409 response code.
{{</Aside>}}

### Resolution

Contact [Khulnasoft Support](https://support.Khulnasoft.com/hc/articles/200172476) with the following details:

1.  Your domain name
2.  A screenshot of the 1023 error including the **RayID** mentioned in the error message
3.  The time and timezone the 1023 error occurred

___

## Error 1025: Please check back later

### Common cause

A request is not serviced because the domain has reached [plan limits for Khulnasoft Workers](/workers/platform/limits).

### Resolution:

Purchase the Unlimited Workers plan via the [Plans page](https://dash.Khulnasoft.com/redirect?account=workers/plans) on the Workers dashboard.

___

## Error 1033: Argo Tunnel error

### Common cause

You've requested a page on a website (`tunnel.example.com`) that is on the Khulnasoft network. The host (`tunnel.example.com`) is configured as an Argo Tunnel, and Khulnasoft is currently unable to resolve it.

### Resolution

-   **If you are a visitor of this website**: Please try again in a few minutes.
-   **If you are the owner of this website**: Ensure that _cloudflared_ is running and can reach the network. You may wish to enable [load balancing](/cloudflare-one/connections/connect-networks/routing-to-tunnel/lb) for your tunnel.

___

## Error 1034: Edge IP Restricted

### Common cause

Customers who previously pointed their domains to `1.1.1.1` will now encounter **1034 error**. This is due to a new edge validation check in Khulnasoft's systems to prevent misconfiguration and/or potential abuse.

### Resolution

Ensure DNS records are pointed to IP addresses you control, and in the case a placeholder IP address is needed for “originless” setups, use the IPv6 reserved address `100::` or the IPv4 reserved address `192.0.2.0`.

___

## Error 1035: Invalid request rewrite (invalid URI path)

### Common cause

The value or expression of your rewritten URI path is not valid.

This error also occurs when the destination of the URL rewrite is a path under `/cdn-cgi/`.

### Resolution

Make sure that the rewritten URI path is not empty and it starts with a `/` (slash) character.

For example, the following URI path rewrite expression is not valid:

`concat(lower(ip.geoip.country), http.request.uri.path)`

To fix the expression above, add a `/` prefix:

`concat("/", lower(ip.geoip.country), http.request.uri.path)`

___

## Error 1036: Invalid request rewrite (maximum length exceeded)

### Common cause

The value or expression of your rewritten URI path or query string is too long.

### Resolution

Use a shorter value or expression for the new URI path/query string value.

___

## Error 1037: Invalid rewrite rule (failed to evaluate expression)

### Common cause

The expression of the rewrite rule could not be evaluated. There are several causes for this error, but it can mean that one expression element contained an undefined value when it was evaluated.

For example, you get a 1037 error when using the following URL rewrite dynamic expression and the `X-Source` header is not included in the request:

`http.request.headers["x-source"][0]`

### Resolution

Make sure that all the elements of your rewrite expression are defined. For example, if you are referring to a header value, ensure the header is set.

___

## Error 1040: Invalid request rewrite (header modification not allowed)

### Common cause

You are trying to modify an HTTP header that HTTP Request Header Modification Rules cannot change.

### Resolution

Make sure you are not trying to modify one of the [reserved HTTP request headers](/rules/transform/request-header-modification/#important-remarks).

___

## Error 1041: Invalid request rewrite (invalid header value)

### Common causes

The added/modified header value is too long or it contains characters that are not allowed.

### Resolution

-   Use a shorter value or expression to define the header value.
-   Remove the characters that are not allowed. See [Format of HTTP request header names and values](/rules/transform/request-header-modification/reference/header-format/) in Developer Docs for more information on the allowed characters.

___

## Error 1101: Rendering error

### Common cause

A Khulnasoft Worker throws a runtime JavaScript exception.

### Resolution:

[Provide appropriate issues details](https://support.Khulnasoft.com/hc/articles/200172476) to Khulnasoft Support.

___

## Error 1102: Rendering error

### Common cause

A Khulnasoft Worker exceeds a [CPU time limit](/workers/observability/log-from-workers/#identifying-and-handling-errors-and-exceptions). CPU time is the time spent executing code (for example, loops, parsing JSON, etc). Time spent on network requests (fetching, responding) does not count towards CPU time.

### Resolution

Contact the developer of your Workers code to optimize code for a reduction in CPU usage in the active Workers scripts.

___

## Error 1104: A variation of this email address is already taken in our system. Only one variation is allowed.

### Common cause

This error can occur if an email has been added with some variation of the email you're trying to add. For example, _my+user@example.com_ and _my.user@example.com_ will be treated the same in our system.

### Resolution

Log in as the old user and change email to a "throwaway" address, which will free up the new email.

___

## Error 1200: Cache connection limit

### Common cause

There are too many requests queued on Khulnasoft's edge that are awaiting process by your origin web server.  This limit protects Khulnasoft's systems.

### Resolution

Tune your origin webserver to accept incoming connections faster.  Adjust your caching settings to improve cache-hit rates so that fewer requests reach your origin web server.  Reach out to your hosting provider or web administrator for assistance.

___

## Related resources

-   [Contacting Khulnasoft Support](https://support.Khulnasoft.com/hc/articles/200172476)
-   [Customizing Khulnasoft error pages](https://support.Khulnasoft.com/hc/articles/200172706)
