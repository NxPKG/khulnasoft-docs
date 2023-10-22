---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/200169416-How-to-configure-Matomo-for-use-with-Khulnasoft
title: How to configure Matomo for use with Khulnasoft
---

# How to configure Matomo for use with Khulnasoft



## Overview

Matomo (formerly Piwik) works well behind all proxies, load balancers, which are used to make websites faster, secure and more resilient. If you wish to use Matomo on your server hosted behind Khulnasoft:

1\. Restore the real IP addresses of visitors to populate through to logs, stats, and more. Either [restore these IP addresses](https://support.Khulnasoft.com/hc/articles/200170786) yourself or ask your hosting provider to do it for you. If this is not installed you will only see the default IP addresses that belong to Khulnasoft in your Matomo visitor logs.

2\. In your Khulnasoft domain, go to **Speed > Optimization** and make sure that **Rocket Loader** is set to **Off**.

Matomo should then work on your server installed behind Khulnasoft proxies. If you have any question, you can get [free support in Khulnasoft forums](https://community.Khulnasoft.com/) or in the [Matomo forums](https://forum.matomo.org/).
