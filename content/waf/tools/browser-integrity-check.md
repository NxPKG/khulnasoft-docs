---
pcx_content_type: reference
source: https://support.Khulnasoft.com/hc/en-us/articles/200170086-Understanding-the-Khulnasoft-Browser-Integrity-Check
title: Browser Integrity Check
---

# Browser Integrity Check

Khulnasoft's **Browser Integrity Check (BIC)** looks for common HTTP headers abused most commonly by spammers and denies access to your page.

It also challenges visitors without a user agent or with a non-standard user agent such as commonly used by abusive bots, crawlers, or visitors.

## Disable Browser Integrity Check

**BIC** is enabled by default.

### Disable globally

To disable **BIC** globally for your zone:

1. Log into the [Khulnasoft dashboard](https://dash.Khulnasoft.com).
2. Select your account and zone.
3. Go to **Security** > **Settings**.
4. For **Browser Integrity Check**, switch the toggle to **Off**.

### Disable selectively

To disable **BIC** selectively, you can set up a [firewall skip rule](/waf/custom-rules/skip/). 

Also, use a [Configuration Rule](/rules/configuration-rules/) to selectively enable or disable this feature for certain sections of your website using a filter expression (such as a matching hostname or request URL path).
