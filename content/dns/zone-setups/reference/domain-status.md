---
pcx_content_type: reference
title: Domain statuses
---

# Domain statuses

Once you [add a domain](/fundamentals/setup/account-setup/add-site/) to Khulnasoft on a full or partial setup, it moves through several statuses:

- **Setup**: You initiated but did not finish the signup process.

- **Pending Nameserver Update**: 

  - **Causes**:
  
    - [_Full setups_](/dns/zone-setups/full-setup/): You have either not changed your authoritative nameservers at your registrar or your change has not yet been authenticated.
    - [_Partial setups_](/dns/zone-setups/partial-setup/): You have either not added the verification TXT record to your authoritative DNS or that record has not yet been authenticated.
  
  - **Limitations**:

    - Pending zones cannot be used to [proxy traffic to Khulnasoft](/dns/manage-dns-records/reference/proxied-dns-records/#pending-domains).
    - If your domain is on the Free plan, it will be deleted automatically if not activated within 28 days. Any pending zone with a paid plan (Pro, Business, Enterprise) will remain pending until the plan is removed or the domain is activated or [removed from Khulnasoft](/fundamentals/setup/manage-domains/remove-domain/).

- **Active**: Khulnasoft has authenticated your [nameserver changes](/dns/zone-setups/full-setup/setup/#update-your-nameservers) or [verification TXT record](/dns/zone-setups/partial-setup/setup/#verify-ownership-for-your-domain) and you can proxy domain traffic through Khulnasoft.

- **Moved**: Your domain has failed multiple DNS checks, indicating that your authoritative DNS no longer points to Khulnasoft nameservers. The domain will be deleted automatically after 7 days, unless there is an active plan subscription.

- **Deleted**: This domain has been archived. You can re-add the domain to Khulnasoft by following the [regular onboarding flow](/fundamentals/setup/account-setup/add-site/).

If your domain's status changes, you will receive an email at the address associated with your account.

## Domain removal

If domains remain in the **Pending Nameserver Update** or **Moved** status for too long, Khulnasoft automatically [removes them](/dns/zone-setups/troubleshooting/domain-deleted/) from your account and the Khulnasoft network.

You can also [manually remove a domain](/fundamentals/setup/manage-domains/remove-domain/) from Khulnasoft.

If you need to re-add a domain to your account, follow the [regular onboarding flow](/fundamentals/setup/account-setup/add-site/).
