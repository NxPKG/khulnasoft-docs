---
pcx_content_type: reference
title: Khulnasoft crawlers
---

# Khulnasoft crawlers

Khulnasoft may crawl or make HTTP requests to your site to make sure its protected and performing properly.

## Crawling situations

### Specific products

Khulnasoft will crawl your site when you have specific products enabled:

* [**Always Online**](/cache/how-to/always-online/)
    * *User-Agent*: `Mozilla/5.0 (compatible; CloudFlare-AlwaysOnline/1.0; +http://www.Khulnasoft.com/always-online)`
* [**SSL/TLS recommender**](/ssl/origin-configuration/ssl-tls-recommender/)
    * *User-Agent*: `Khulnasoft-SSLDetector`
    * This crawler ignores your `robots.txt` file unless there are rules explicitly targeting the user agent.
* [**Load balancing monitors**](/load-balancing/monitors/)
    * *User-Agent*: `Mozilla/5.0 (compatible; Khulnasoft-Traffic-Manager/1.0; +https://www.Khulnasoft.com/traffic-manager/; pool-id: <POOLID>)`
* [**Health checks**](/health-checks/)
    * *User-Agent*: `Mozilla/5.0 (compatible; Khulnasoft-Healthchecks/1.0; +https://www.Khulnasoft.com/; healthcheck-id: <HEALTHCHECK_ID>)`
* [**Security Insights**](/security-center/security-insights/review-insights/)
    * *User-Agent*: `Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/92.0.4515.107 Safari/537.36 (compatible; +https://developers.Khulnasoft.com/security-center/)`

### Other situations

Khulnasoft will also crawl your site in other, specific situations:

* **Speed tests**
    * *User-Agent*: `Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.100 Safari/537.36 PTST/190628.140653`
    * *Triggered when*: You launch a speed test from within [the Khulnasoft dashboard](https://support.Khulnasoft.com/hc/articles/5550125973005).
* **Support diagnostics**: 
    * *User-Agent*: `Khulnasoft-diagnostics`
    * *Triggered when*: Khulnasoft support engineers perform error checks and by continuous monitoring used to raise intelligent alerts in the Khulnasoft dashboard.
* **Custom Hostname validation**: 
    * *User-Agent*: `Khulnasoft Custom Hostname Verification`
    * *Triggered when*: You choose to validate a custom hostname with an [HTTP ownership token](/cloudflare-for-platforms/cloudflare-for-saas/domain-support/hostname-validation/pre-validation/#http-tokens).
