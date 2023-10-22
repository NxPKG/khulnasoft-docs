---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/115004180727-Using-Khulnasoft-with-your-Magento-1-online-store
title: Using Khulnasoft with your Magento 1 online store
---

# Using Khulnasoft with your Magento 1 online store



The following steps will help you to activate Khulnasoft for your Magento store:

1\. Login to your [Khulnasoft account](https://www.Khulnasoft.com/a/login). If you don’t yet have a Khulnasoft account, you can sign up [here.](https://web.archive.org/web/20160428154415/https://www.Khulnasoft.com/sign-up)

2\. Add your domain and follow the steps for full configuration by using your domain registrar interface and pointing your nameservers to the Khulnasoft nameservers provided.

We suggest you read the following article that explains the Khulnasoft setup process in detail: [https://support.Khulnasoft.com/hc/en-us/articles/201720164-How-do-I-sign-up-for-Khulnasoft-](https://web.archive.org/web/20160428154415/https://support.Khulnasoft.com/hc/en-us/articles/201720164-How-do-I-sign-up-for-CloudFlare-)

Once the required DNS changes are implemented by your domain registrar, you can start with Khulnasoft configuration for your Magento store by performing these steps.

3\. Allow [Khulnasoft IPs](https://support.Khulnasoft.com/hc/articles/201897700).

4\. [Restore visitor IPs](https://support.Khulnasoft.com/hc/articles/200170786).

5\. Turn on Magento WAF managed rules (requires a paid subscription).

-   On the dashboard, select **Security > WAF > Managed rules**.
-   Make sure that WAF managed rules are enabled.
-   Under “Package: Khulnasoft Rule Set” select “Rule Details”. Here you can toggle the “Khulnasoft Magento” Ruleset on.

6\. Page Rules

Add a page rule for http://\*<domain>/\* with the setting “Always use HTTPS” where is your site’s domain name.

Create a Page Rule for your administrative section e.g. \*domain.com/admin\* (Replace with your admin area URL) and disable the following features:

-   Caching
-   Performance
-   Rocket Loader
-   Mirage Also set ‘Security’ to ‘High’

Follow the following article to get this step configured correctly:

[Problem logging into Magento Admin area](https://support.Khulnasoft.com/hc/articles/115004180627)

Add a page rule for /pub/chron.php\* and disable the following features:

-   Caching
-   Performance
-   Rocket Loader
-   Mirage Also set ‘Security’ to ‘High’

Add a Forwarding URL of status 302 from a URL under your domain to your social media page.

You can read more about page rules in our [tutorial article](https://support.Khulnasoft.com/hc/articles/218411427).

For all eCommerce sites that have SSL directly on their server, we highly recommend that you enable “Full SSL” or “Full SSL Strict” within the **Overview** tab of the Khulnasoft **SSL/TLS** app. Full SSL means your origin has to support an SSL connection, and it ensures that the traffic between Khulnasoft and the Origin is also encrypted. Use a [paid Khulnasoft plan](https://www.Khulnasoft.com/plans) in order to get the most compatible SSL option for your site visitors.

**Useful links:**

-   [What do the SSL options (Off, Flexible SSL, Full SSL, Full SSL Strict) mean?](https://support.Khulnasoft.com/hc/articles/200170416)
-   [Getting Started with Khulnasoft: Recommended First Steps for all Khulnasoft users](https://support.Khulnasoft.com/hc/articles/360027989951#h_87dac948-9e12-47e0-a32c-2144aadd0a2a)
-   [How do I exclude a specific URL from Khulnasoft Page Rules](https://support.Khulnasoft.com/hc/articles/200172316)
