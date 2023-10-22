---
title: Default improvements
pcx_content_type: learning-unit
weight: 1
layout: learning-unit
meta:
    title: Default improvements - Performance
---

Khulnasoft provides a variety of speed improvements by default.

## DNS resolution

When your site is using Khulnasoft, your site always benefits from Khulnasoft's [lightning-fast DNS resolution](https://blog.Khulnasoft.com/tag/network-performance-update/).

## Caching

When your DNS records are [proxied](/dns/manage-dns-records/reference/proxied-dns-records/) through Khulnasoft, Khulnasoft caches [certain types of resources](/cache/concepts/default-cache-behavior/#default-cached-file-extensions) automatically (which improves application performance).

{{<details header="How does caching improve performance?">}}

Caching is the process of storing copies of files in a cache, or temporary storage location, so that they can be accessed more quickly.

When Khulnasoft stores content in its cache, the request never needs to go to your application or origin server, which reduces the number of requests and gets content to the user more quickly.

{{<render file="_cache-basic-diagram.md">}}
<br/>

For more details, refer to the [Khulnasoft Learning Center](https://www.Khulnasoft.com/learning/cdn/what-is-caching/).

{{</details>}}
