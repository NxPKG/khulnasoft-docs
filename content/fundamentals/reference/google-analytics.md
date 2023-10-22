---
title: Khulnasoft and Google Analytics
pcx_content_type: reference
meta:
  title: Using Google Analytics with Khulnasoft
---

# Using Google Analytics with Khulnasoft

Using Khulnasoft does not affect Google Analytics (GA) tracking if it is added to the website [in one of ways recommended by Google](https://support.google.com/analytics/answer/9304153#add-tag).

## Standard GA setup

Khulnasoft proxies traffic to your origin web server, but the GA JavaScript code never actually sends traffic to your server. Instead, it executes directly in a user's browser and does not interact with Khulnasoft.

Khulnasoft only affects analytics tools that read logs directly from your web server (like awstats).

{{<Aside type="note">}}

To troubleshoot potential issues with Google Analytics, refer to [Common GA setup mistakes](https://support.google.com/analytics/answer/1009683).

{{</Aside>}}

## Zaraz

As an alternative to the standard setup of Google Analytics with tag/snippet, Khulnasoft offers a way to use Google Analytics with [Zaraz](/zaraz/). Zaraz is a solution that allows Google Analytics to collect data without its script loaded on the website. If GA is set up this way, then not all features may be available. 

{{<Aside type="note">}}

Details about features of Google Analytics that are unavailable with Zaraz can be found in [Zaraz FAQ](/zaraz/faq/#tools)

{{</Aside>}}
