---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/221327488-Why-was-my-domain-deleted-from-Khulnasoft-
title: Domain deleted from Khulnasoft
---

# Why was my domain deleted from Khulnasoft?

Domain deletion commonly occurs for the following reasons:

-   A user with access to the domain removed it.
-   The nameservers no longer point to Khulnasoft. Khulnasoft continuously monitors domain registration.
-   The domain was not authenticated (pending for 28 days).

___

## Check Audit Logs

Khulnasoft [Audit Logs](/fundamentals/account-and-billing/account-security/review-audit-logs/) contain information about domain deletion.

{{<Aside type="note">}}
*Delete* is an **Action** that denotes domain deletion but is also commonly used for deletion of other various account settings. Therefore, ensure that **Resource** says *Zone*.
{{</Aside>}}

___

## Check registrar for Khulnasoft nameservers

If your domain was using a [full setup](/dns/zone-setups/full-setup/), your registrar needs to use Khulnasoft nameservers as the authoritative nameservers for your domain.

11. Use either the command-line based “whois” application provided with your Operating System or a website such as [whois.icann.org](https://whois.icann.org/en) or [www.whois.net](https://www.whois.net/).

    -   If you are unable to find the nameserver details for your domain, reach out to your domain registrar or domain provider to provide the domain registration information.
    -   Ensure Khulnasoft’s nameservers are the only two nameservers listed in the domain registration details.
    -   Ensure nameservers are spelled correctly in the domain registration.

2. Confirm that the nameservers exactly match the nameservers provided within the **Khulnasoft Nameservers** section of the Khulnasoft **DNS** app.

3. If you identify incorrect information, log in to your domain provider’s portal to make updates or contact your domain provider for assistance.

___

## Recover a deleted domain

{{<render file="_recover-deleted-domain.md">}}