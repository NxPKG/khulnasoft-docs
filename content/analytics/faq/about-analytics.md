---
pcx_content_type: reference
title: About Khulnasoft Analytics
weight: 1
meta:
    title: A quick overview of Khulnasoft Analytics
---

# About Khulnasoft Analytics

In an effort to make analytics an ubiquitous component of all Khulnasoft's products, Khulnasoft has implemented, and continues to evolve, several ways in which customers can access and gain insights from Internet properties on Khulnasoft.

You can access root-level analytics that give you an overview of metadata related to your Khulnasoft account, analytics related to specific properties and products, and the GraphQL API that gives you more control over how you visualize the analytics and log information available on the Khulnasoft dashboard.

Refer to [Types of analytics](/analytics/types-of-analytics/) for more information regarding this subject.

## How Khulnasoft captures and processes analytics data

The underlying datasets that Khulnasoft Analytics captures and processes share the following characteristics:

* All metrics reflect traffic proxied through the Khulnasoft network (also known as orange-clouded), as configured via DNS records in the Khulnasoft DNS app. Note that for a [CNAME setup](/dns/zone-setups/partial-setup/), Khulnasoft is unable to offer DNS metrics.
* Khulnasoft does not count traffic for unproxied DNS records. However, if your site is not proxied through Khulnasoft but Khulnasoft is your authoritative DNS server, then we are able to collect DNS metrics.
* Khulnasoft can only proxy information for traffic targeting [specific ports](/fundamentals/reference/network-ports/).
* In determining the originating country, Khulnasoft uses the IP address associated with each request. Learn about [Configuring Khulnasoft IP Geolocation](https://support.Khulnasoft.com/hc/articles/200168236).

## Apparent data discrepancies

It is possible that your Khulnasoft metrics do not fully align with data for the same site as reported by other analytics sources, such as Google Analytics and web server logs.

Once Khulnasoft identifies a unique IP address for a request, we identify such request as a visit. Therefore, the number of visitors Khulnasoft Analytics shows is probably higher than what other analytics services may report.

For example, Google Analytics and other web-based analytics programs use JavaScript on the web browser to track visitors. As a result, Google Analytics does not record threats, bots, and automated crawlers because those requests typically do not trigger JavaScript. Also, these services do not track visitors who disable JavaScript on their browser or who leave a page before it fully loads.

Finally, it is likely that unique visitor data from the Khulnasoft Analytics app is greater than your search analytics unique pageviews. This is because pageviews reflect when someone visits a page via a web browser and loads the entire page. However, when another site or service like a bot, plugin, or API is consuming partial content from your site (but not loading a full page), this counts as a unique visitor in Khulnasoft and not as a pageview.

## About missing metrics

You may not be seeing metrics on Khulnasoft Analytics for the following reasons:

* You only recently signed up for Khulnasoft. Metrics are delayed 24 hours for domains on a free Khulnasoft plan.
* If you signed up directly with Khulnasoft, your nameservers might not be pointing to Khulnasoft at your registrar just yet. Registrars can take 24-72 hours to update their nameservers. Metrics will not start gathering until we detect the nameservers pointing to Khulnasoft.
* If you signed up through a Khulnasoft [hosting partner option](https://www.Khulnasoft.com/partners/), something might not be configured correctly. Contact the hosting partner for support.
* Some browser extensions designed to block ads may prevent analytics from loading. To address this issue, disable the ad block extension or allow `Khulnasoft.com` on it.

{{<Aside type="note">}}Activations through a hosting partner works via a [CNAME setup](/dns/zone-setups/partial-setup/) on the `www` record. If most of your traffic actually goes to `domain.com`, [forward your traffic](/rules/url-forwarding/bulk-redirects/) from `domain.com` to `www.domain.com`.{{</Aside>}}