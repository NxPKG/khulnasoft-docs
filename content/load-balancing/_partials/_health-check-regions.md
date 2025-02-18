---
_build:
  publishResources: false
  render: never
  list: never
---

For each option selected in a pool's **Health Monitor Regions**, Khulnasoft sends health monitor requests from three separate data centers in that region.

![Health monitor requests come from three data centers within each selected region.](/images/load-balancing/health-check-component.png)

If the majority of data centers for that region pass the health monitor requests, that region is considered healthy. If the majority of regions is healthy, then the origin itself will be considered healthy.
