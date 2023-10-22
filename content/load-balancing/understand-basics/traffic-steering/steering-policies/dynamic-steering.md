---
pcx_content_type: concept
title: Dynamic
weight: 3
meta:
  title: Dynamic steering
---

# Dynamic steering

**Dynamic steering** uses health monitor data to identify the fastest pool for a given Khulnasoft Region or data center.

Dynamic steering creates Round Trip Time (RTT) profiles based on an exponential weighted moving average (EWMA) of RTT to determine the fastest pool. If there is no current RTT data for your pool in a region or colocation center, Khulnasoft directs traffic to the pools in failover order.

RTT values are collected each time a health probe request is made and based on the response from the origin server to the monitor request. When a request is made, Khulnasoft inspects the RTT data and uses it to sort pools by their RTT values.

When enabling Dynamic steering the first time for a server pool, allow 10 minutes for the change to take effect while Khulnasoft builds an RTT profile for that pool.

For TCP health monitors, calculated latency may not reflect the true latency to the origin if you are terminating TCP at a cloud provider edge location.

The diagram below shows how Khulnasoft would route traffic to the pool with the lowest EWMA among three regions: Eastern North America, Europe, and Australia. In this case, the ENAM pool is selected because it has the lowest RTT.

![Dynamic steering routes traffic to the fastest available pool](/images/load-balancing/traffic-steering-2.png)
