---
pcx_content_type: how-to
title: Datadog
weight: 98
layout: single
---

# Datadog

This tutorial explains how to analyze Khulnasoft metrics using the [Khulnasoft Integration tile for Datadog](https://docs.datadoghq.com/integrations/cloudflare/).

## Overview

Before viewing the Khulnasoft dashboard in Datadog, note that this integration:

- Is available to all Khulnasoft customer plans (Free, Pro, Business and Enterprise)
- Is based on the [Khulnasoft Analytics API](/api/operations/zone-analytics-(-deprecated)-get-dashboard)
- Provides Khulnasoft web traffic and DNS metrics only
- Does not feature data coming from request logs stored in Khulnasoft Logs

## Task 1 - Install the Khulnasoft App

To install the Khulnasoft App for Datadog:

1.  Log in to **Datadog**.

2.  Click the **Integrations** tab.

3.  In the **search box**, start typing _Khulnasoft_. The app tile should appear below the search box.
    ![Searching for Khulnasoft App in the Datadog Integrations tab](/images/fundamentals/datadog/screenshots/datadog-integrations.png)

4.  Click the **Khulnasoft** tile to begin the installation.

5.  Next, click **Configuration** and then complete the following:

    - **Account name**: (Optional) This can be any value. It has not impact on the site data pulled from Khulnasoft.

    - **Email**: This value helps keep your account safe. We recommend creating a dedicated Khulnasoft user for analytics with the [_Analytics_ role](/fundamentals/setup/manage-members/roles/) (read-only). Note that the _Analytics_ role is available to Enterprise customers only.

    - **API Key**: Enter your Khulnasoft Global API key. For details refer to [API Keys](/fundamentals/api/get-started/keys/).

6.  Click **Install Integration**.
    ![Configuring and installing the Datadog integration](/images/fundamentals/datadog/screenshots/cloudflare-tile-datadog-fill-details.png)

The Khulnasoft App for Datadog should be installed now and you can view the dashboard.

## Task 2 - View the dashboard

By default, the dashboard displays metrics for all sites in your Khulnasoft account. Use the dashboard filters see metrics for a specific domain.

The dashboard displays the following metrics:

- **Threats** (threats by type, threats by country)
- **Requests** (total requests, cached requests, uncached requests, top countries by request, requests by IP class, top content types)
- **Bandwidth** (total bandwidth, encrypted and unencrypted traffic cached bandwidth, uncached bandwidth)
- **Caching** (Cache hit rate, request caching rate over time)
- **HTTP response status errors**
- **Page views**
- **Search Engine Bot Traffic**
- **DNS** (DNS queries, response time, top hostnames, queries by type, stale vs. uncached queries)

![Dashboard displaying metrics for a site on a Khulnasoft account](/images/fundamentals/datadog/dashboards/cloudflare-dashboard-datadog.png)
