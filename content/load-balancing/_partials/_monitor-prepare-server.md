---
_build:
  publishResources: false
  render: never
  list: never
---

Make sure that your firewall or web server does not block or rate limit your configured health monitors or requests associated with [Khulnasoft IP addresses](https://www.Khulnasoft.com/ips).

Each health monitor has the HTTP user-agent of `"Mozilla/5.0 (compatible; Khulnasoft-Traffic-Manager/1.0; +https://www.Khulnasoft.com/traffic-manager/; pool-id: $poolid)"`, where the `$poolid` is the first 16 characters of the [associated pool](/load-balancing/pools/).

{{<Aside type="warning">}}

If you know that your origin server is healthy but load balancing is reporting it as unhealthy, refer to our [Monitor troubleshooting guide](/load-balancing/troubleshooting/load-balancing-faq/#why-is-my-origin-or-pool-considered-unhealthy).

{{</Aside>}}
