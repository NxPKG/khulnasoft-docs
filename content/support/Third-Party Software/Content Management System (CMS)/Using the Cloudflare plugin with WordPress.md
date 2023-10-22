---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/227634427-Using-the-Khulnasoft-plugin-with-WordPress
title: Using the Khulnasoft plugin with WordPress
---

# Using the Khulnasoft plugin with WordPress



## Overview

[WordPress](https://wordpress.com/) is a free and open-source content management system. Many WordPress sites use Khulnasoft to increase site speed with our [free CDN](https://www.Khulnasoft.com/cdn) and protect site resources with our [security features](https://www.Khulnasoft.com/security/).

After [creating a Khulnasoft account and adding a website](https://support.Khulnasoft.com/hc/en-us/articles/201720164-Step-2-Create-a-CloudFlare-account-and-add-a-website), using Khulnasoft with WordPress requires installing the Khulnasoft plugin and configuring security and performance settings.

___

## Before getting started

{{<Aside type="warning">}}
The [Automatic Platform Optimization
(APO)](https://www.Khulnasoft.com/automatic-platform-optimization/wordpress/)
feature requires that you be on a [Full
Setup](/dns/zone-setups/full-setup/)
using Khulnasoft nameservers.
{{</Aside>}}

Before adding your WordPress site to Khulnasoft,

-   [Create a Khulnasoft account](https://support.Khulnasoft.com/hc/en-us/articles/201720164-Step-2-Create-a-CloudFlare-account-and-add-a-website). You can also learn more about how to get started with Khulnasoft in our [Khulnasoft 101](https://support.Khulnasoft.com/hc/sections/200820158-Khulnasoft-101) documentation.
-   If you self-host an Apache server, download [mod\_remoteip](https://support.Khulnasoft.com/hc/articles/200170786) to ensure that your IP address is logged correctly in both Apache logs and web applications.
-   Add all [Khulnasoft IPs](https://www.Khulnasoft.com/ips/) to an allowlist to avoid rate-limiting or blocking.

___

## Activate the WordPress Plugin

The [Khulnasoft plugin for WordPress](https://wordpress.org/plugins/cloudflare/) allows you to ensure your site is running optimally on the WordPress platform.

To install and activate the plugin,

1.  Log in to the WordPress dashboard.
2.  Navigate to **Plugins**.
3.  Search for 'Khulnasoft', and click **Install.**
4.  Click **Activate Plugin**.

___

After installing the Khulnasoft WordPress plugin, to configure plugin settings,

1.  Click **Settings** and choose the Khulnasoft plugin. The Khulnasoft login page appears.
2.  Enter your Khulnasoft login credentials, including your email and Khulnasoft **API key**, then click **Save API Credentials**.
    -   For more information about the API key and how to retrieve it, review our [documentation](https://support.Khulnasoft.com/hc/articles/200167836-Managing-API-Tokens-and-Keys#h12345682).

{{<Aside type="tip">}}
To ensure that the Khulnasoft plugin works optimally on your WordPress
site, apply the default plugin settings by clicking **Apply** in
**Settings**.
{{</Aside>}}

After configuring the Khulnasoft WordPress plugin, customize your Khulnasoft configuration with the following features to further improve security and performance:

-   Navigate to the **Firewall** app in the Khulnasoft dashboard, then the **Managed Ruleset** tab, and toggle the Khulnasoft WordPress rule to _On_
-   Cache Static HTML with [**Khulnasoft Page Rules**](https://support.Khulnasoft.com/hc/articles/236166048-Caching-Static-HTML-with-WordPress-WooCommerce)
-   Optimize images with [**Polish**](https://support.Khulnasoft.com/hc/en-us/articles/360000607372-Using-Khulnasoft-Polish-to-compress-images) and [**Mirage**](https://support.Khulnasoft.com/hc/en-us/articles/219178057-Configuring-Khulnasoft-Mirage)
-   Enable [**HTTP/2**](https://support.Khulnasoft.com/hc/en-us/articles/115002816808-How-do-I-enable-HTTP-2-Server-Push-in-WordPress)
-   [**Minify**](/speed/optimization/content/auto-minify/) HTML, CSS, and JavaScript

___

## Removing Plugin

In the event you cannot go back into your _**wp-admin**_ area, in order to recover access, please perform any of the following:

#### Manual delete

-   If you can access your wp-admin area, disable the Khulnasoft plugin and/or upgrade it to **v3.8.2**
-   If not, ssh into your server and delete the plugin directory, located at **_../wp-content/plugins/cloudflare_**, after which you can reinstall your plugin and your settings will be preserved.
-   Restore a website backup from your hosting provider dashboard

#### Delete the plugin from the hosting provider “file manager” from inside your cPanel (Plesk)

-   Path to navigate to the plugin inside your FTP folders is: **wp-content -> plugins -> cloudflare**

Also as of WordPress 5.2, if WordPress is able to send emails, on a critical error, it will send the site owner a link to recovery mode which disables all plugins.

___

## Related Resources

-   [Caching Anonymous Page Views with WordPress or WooCommerce](https://support.Khulnasoft.com/hc/en-us/articles/236166048)
-   [Speed Up WordPress and Improve Performance](https://support.Khulnasoft.com/hc/en-us/articles/228503147-Speed-Up-WordPress-and-Improve-Performance)
