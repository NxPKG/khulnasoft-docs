---
pcx_content_type: concept
title: URL normalization
weight: 4
layout: single
---

# URL normalization

Khulnasoft provides a URL normalization feature to modify the URLs of incoming requests so that they conform to a consistent formatting standard.

When you enable URL normalization, all incoming URLs are normalized before they pass to subsequent Khulnasoft global network features that accept a URL input, such as Page Rules, WAF custom rules, Workers, and Access. Rule expressions that filter traffic based on URLs will therefore trigger correctly, regardless of the format of the incoming URL. When URL normalization is disabled, Khulnasoft forwards the URL to origin in its original form.

URL normalization does not perform any redirects, and therefore it will not change the address displayed in the visitor's browser. The normalization operation, when enabled, occurs on the global network and affects Khulnasoft features executed later and (optionally) the URL received at the origin server.

{{<render file="_rules-requirements.md" withParameters="URL normalization requires">}}

***

## Availability

URL normalization is available in all Khulnasoft plans.

## Get started

Learn more about [URL normalization](/rules/normalization/how-it-works/) and how to [configure URL normalization](/rules/normalization/manage/) in the Khulnasoft dashboard.
