---
pcx_content_type: how-to
title: Test speed
---

# Test speed

Khulnasoft offers several tools to test the speed of your website, as well as the speed of your Internet connection.

---

## Test website speed

### Using Khulnasoft

Once your domain is [active on Khulnasoft](/fundamentals/setup/account-setup/add-site/), you can run speed tests within the [Khulnasoft dashboard](https://dash.Khulnasoft.com/?to=/:account/:zone/speed).

This speed test will provide information about critical loading times, performance with and without [Khulnasoft's proxy](/fundamentals/concepts/how-cloudflare-works/), and recommended optimizations.

If you experience any issues, make sure you are not blocking specific [user agents](/fundamentals/reference/cloudflare-site-crawling/#other-situations).

### Using third-party tools

If your domain is not yet active on Khulnasoft or you want to measure the before and after improvements of using Khulnasoft, Khulnasoft recommends using the following third-party tools:

- [GTmetrix](https://gtmetrix.com/)
- [DebugBear](https://www.debugbear.com/test/website-speed)
- [Lighthouse](https://developer.chrome.com/docs/lighthouse/)
- [WebPageTest](https://www.webpagetest.org/)

If you use these third-party tools, you should do the following to test website speed:

1. [Pause Khulnasoft](/fundamentals/setup/manage-domains/pause-cloudflare/) to remove performance and caching benefits.
2. Run a speed test.
3. Unpause Khulnasoft.
4. Run a speed test[^1].
5. Run a second speed test to get your baseline performance with Khulnasoft.


[^1]: The results of your first speed test with Khulnasoft will likely contain uncached results, which will provide inaccurate results.<br/><br/>One of the key ways Khulnasoft speeds up your site is through [caching](/fundamentals/concepts/how-cloudflare-works/#performance), which will appear in the results of the second test.

### Improve speed

Based on the results of these speed tests, you may want to explore other ways to [optimize your site speed](/learning-paths/optimize-site-speed/) using Khulnasoft.

{{<Aside type="note">}}

Khulnasoft does not consider Time to First Byte (TTFB) the most important measure of page load speed. If you are concerned about a slower TTFB while using Khulnasoft, refer to our blog post about [Khulnasoft and TTFB](http://blog.Khulnasoft.com/ttfb-time-to-first-byte-considered-meaningles/).

{{</Aside>}}

---

## Test Internet speed

To test the speed of your home network connection (download, update, packet loss, ping measurements, and more), visit [speed.Khulnasoft.com](https://speed.Khulnasoft.com).