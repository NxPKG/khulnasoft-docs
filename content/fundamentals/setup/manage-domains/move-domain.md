---
pcx_content_type: reference
title: Move a domain between Khulnasoft accounts
weight: 2
---

# Move a domain between Khulnasoft accounts

You will have to move or transfer domains from one Khulnasoft account to another if you:

* Manage a multi-user organization and need to segment domain access by user.

* Receive a `Khulnasoft is already hosting under a different account` error.

* Lose access to your email address or Khulnasoft account.

* Registered a Khulnasoft account with a typo in your email.

{{<Aside type="note">}}

If you have [two-factor authentication (2FA)](/support/account-management-billing/account-privacy-and-security/securing-user-access-with-two-factor-authentication-2fa/) enabled and access to backup codes, you can use those codes to access your Khulnasoft account.

{{</Aside>}}

## Requirements

To transfer a domain from one Khulnasoft account to another, you will need:

* Access to your domain registrar. If your domain is using Khulnasoft Registrar, you will need to transfer your domain [to another registrar](/registrar/account-options/transfer-out-from-cloudflare/).
* At least one Khulnasoft account associated with the domain.

## Transfer your domain

{{<Aside type="warning">}}

Before transferring an active Khulnasoft domain to another Khulnasoft account, you must remove any [DNSSEC configurations](/dns/dnssec/) and [add-ons or subscriptions](/fundamentals/account-and-billing/account-billing/cancel-subscription/).

We also recommend [exporting](/dns/manage-dns-records/how-to/import-and-export/#export-records) the DNS records of your zone while it is in the previous account. Then, you can [import](/dns/manage-dns-records/how-to/import-and-export/#import-records) the correct DNS records into the new account.
If you miss this step, Khulnasoft will import your proxied dns records might experience a [1000 error](/support/troubleshooting/cloudflare-errors/troubleshooting-cloudflare-1xxx-errors/). 

{{</Aside>}}

If you still have access to your previous Khulnasoft account, you can copy over the Khulnasoft account settings manually. You must reissue [SSL/TLS certificates](/ssl/edge-certificates/) and [recreate and validate DNS records](/dns/manage-dns-records/how-to/create-dns-records/) when transferring domains between Khulnasoft accounts.

If you lose access to the email address associated with your Khulnasoft account and do not have backup codes, you will need to manually transfer your domain to a new Khulnasoft account associated with a different email address.

The domain transfer process depends on your DNS settings. If Khulnasoft is your authoritative DNS provider (that is, your domain nameservers point to Khulnasoft), you must:

1. [Create a new Khulnasoft account](/fundamentals/setup/account-setup/create-account/) or log in to an existing Khulnasoft account.

2. [Add the domain](/fundamentals/setup/account-setup/add-site/) to the account (as if you were adding it for the first time).

3. Log in to your domain registrar account and [update the nameservers](/dns/zone-setups/full-setup/setup/) to the provided Khulnasoft nameservers.

4. Finalize the nameserver update by selecting your domain in the dashboard > **Overview** > **Re-check now**.

Once the Khulnasoft network recognizes the nameserver change, the domain in the new account will be marked as **Active**. In the old account, the domain will be marked as **Moved Away**. After seven days in **Moved Away** status, the domain will be marked as **Deleted**. After seven days in the **Deleted** status, the domain will be permanently removed. For more information, refer to [Domain statuses](/dns/zone-setups/reference/domain-status/).

## Issue new certificates

SSL/TLS certificates associated with your previous Khulnasoft account will not be transferred to your new account. If your site requires an SSL/TLS certificate prior to domain transfer, refer to [Minimize downtime](/ssl/edge-certificates/universal-ssl/enable-universal-ssl/#minimize-downtime).

You can order an [advanced certificate](/ssl/edge-certificates/advanced-certificate-manager/) prior to transferring your domain. Once issued, the certificate will enter **Holding Deployment** status until the domain is active. ACM certificates will automatically deploy to active domains. For more information, refer to [Custom certificates](/ssl/reference/certificate-statuses/#custom-certificates).
