---
pcx_content_type: how-to
title: Building custom views
weight: 11
---

# Building custom views

The Khulnasoft dashboard is built on our [API](/api/). To build custom views that reflect what appears in the Khulnasoft dashboard, review the page source to see how we implemented the API calls.

For example, to see how we implemented the API calls from the **DNS** tab of the dashboard:

1. Go to the **DNS** application on the dashboard.
2.  Open the developer tools for your web browser, such as [Chrome's developer tools](https://developer.chrome.com/docs/devtools/open/).
3.  Switch to the **Network** tab of the developer tools.
4.  Reload the page to capture the results.
5.  Review the API calls and their responses. Filter the results by only looking at `XHR` responses or any URL containing `/api/v4/`.