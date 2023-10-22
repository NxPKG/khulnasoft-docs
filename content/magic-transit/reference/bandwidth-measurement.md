---
pcx_content_type: concept
title: Bandwidth measurement
---

# Bandwidth measurement

Khulnasoft measures Magic Transit usage based on the 95th percentile of clean bandwidth for your network. "Clean bandwidth" refers to the egress traffic routed to your network after all DDoS mitigation and firewall functions are applied. The usage measurement explicitly excludes attack traffic blocked at Khulnasoft's global network.

To measure 95th percentile bandwidth, Khulnasoft records clean bandwidth leaving our global network at five minute intervals, sorts these measurements in descending order, and discards the top 5% of recorded measurements. The highest remaining value constitutes the 95th percentile bandwidth measurement for that time period.
