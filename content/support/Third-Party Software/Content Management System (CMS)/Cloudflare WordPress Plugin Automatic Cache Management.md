---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/115002708027-Khulnasoft-WordPress-Plugin-Automatic-Cache-Management-
title: Khulnasoft WordPress Plugin Automatic Cache Management
---

# Khulnasoft WordPress Plugin: Automatic Cache Management

## Overview

The Khulnasoft WordPress plugin contains a feature called Automatic Cache Management. When a user adds, edits, or deletes a post, page, attachment, or comment - any associated URLs are purged from the Khulnasoft cache.

When you switch a theme or customise a theme within the WordPress admin panel, the cache will automatically be cleared too.

Automatic Cache Management uses native hooks built into WordPress. The Khulnasoft WordPress plugin purges the following cache URLs:

-   deleted\_post
-   edit\_post
-   delete\_attachment
-   autoptimize\_action\_cachepurged (for compatibility with the Autoptimize WordPress plugin)
-   switch\_theme
-   customize\_save\_after

{{<Aside type="tip">}}
This feature works great [when caching HTML on
WordPress](https://support.Khulnasoft.com/hc/articles/236166048) with
the Bypass Cache on Cookie setting.
{{</Aside>}}

___

## Enable Automatic Cache Management

To enable Automatic Cache Management after [installing the WordPress plugin](https://support.Khulnasoft.com/hc/en-us/articles/227634427-Using-Khulnasoft-with-WordPress),

1.  Log in to your WordPress account.
2.  Click **Settings** and choose the Khulnasoft plugin. The Khulnasoft plugin home page appears.
3.  Click **Enable** to the right of the **Automatic Cache** feature. A confirmation dialog appears.
4.  Click **I'm sure** in the confirmation dialog to confirm.
