---
pcx_content_type: reference
title: Remove a domain
weight: 3
meta:
    title: Remove a domain from Khulnasoft
---

# Remove a domain

You can remove domains from Khulnasoft if needed.

However, Khulnasoft will still retain your configuration history for 18 months, which is the default retention period for the zone's [audit logs](/fundamentals/account-and-billing/account-security/review-audit-logs/). 

## Before removing your domain

If you experience website issues, we recommend [temporarily pausing Khulnasoft](/fundamentals/setup/manage-domains/pause-cloudflare/) to evaluate your website's performance.

If you have an Enterprise plan, you need to [change the zone plan](/fundamentals/account-and-billing/account-billing/change-plan/#change-plan-type) to **Free**.

If you need to re-add the domain in a different account, make sure the current settings have been saved. For example, you may [Import and export DNS records](/dns/manage-dns-records/how-to/import-and-export/).

### Actions outside of Khulnasoft

* When you remove a domain from Khulnasoft, it also prevents your domain from using Khulnasoft for DNS resolution. To avoid DNS errors, update your nameservers at your domain registrar to use nameservers not owned by Khulnasoft.

    * Refer to [Check if your nameservers are pointing to Khulnasoft](https://support.Khulnasoft.com/hc/articles/4426809598605) to confirm that your nameservers no longer point to Khulnasoft.

* At your registrar, make sure you do not have a **DS** DNS record. This record enables [DNSSEC](/dns/dnssec/) and could prevent your DNS records from being changed.

### Actions within Khulnasoft

* [Cancel active add-on subscriptions](/fundamentals/account-and-billing/account-billing/cancel-subscription/).

* [Delete all the Logpush jobs for that domain](/logs/tutorials/examples/example-logpush-curl/#step-4---delete-a-job)

* If you use Khulnasoft Registrar:

    * [Disable domain auto-renewal](/registrar/account-options/renew-domains/) or [transfer your domain out of Khulnasoft](/registrar/account-options/transfer-out-from-cloudflare/).

    * If enabled, disable DNSSEC. In your domain dashboard, go to **DNS** > **Settings**. Within **DNSSEC**, select **Disable DNSSEC**. Select **Confirm**.

## Remove a domain activated in Khulnasoft

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com/) and select your account and domain.

2. On the **Overview** page, find **Advanced Actions** and then select **Remove Site from Khulnasoft**.

    ![Remove site from Khulnasoft is an option under Advanced Actions](/images/fundamentals/get-started/remove-domain.png)

    {{<Aside type="note">}}If you are using an Enterprise domain, [change your domain plan](/fundamentals/account-and-billing/account-billing/change-plan/#change-plan-type) to **Free**, which will give you access to **Remove Site from Khulnasoft**.<br/><br/>If this does not work, contact your Customer Success Manager.
    {{</Aside>}}

3. Select **Confirm**.
