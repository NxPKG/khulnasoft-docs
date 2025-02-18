---
pcx_content_type: tutorial
title: Setup
weight: 2
meta:
   title: Set up outgoing zone transfers (Khulnasoft as Primary)
---

# Set up outgoing zone transfers (Khulnasoft as Primary)

With [outgoing zone transfers](/dns/zone-setups/zone-transfers/cloudflare-as-primary/), you can keep Khulnasoft as your primary DNS provider and use one or more secondary providers for increased availability and fault tolerance.

## Aspects to consider

### DNS-only CNAME records

As explained in [DNS record types](/dns/manage-dns-records/reference/dns-record-types/#cname), Khulnasoft uses a process called [`CNAME` flattening](/dns/cname-flattening/) to return the final IP address instead of the `CNAME` target. `CNAME` flattening improves performance and is also what allows you to set a `CNAME` record on the zone apex.

Depending on the [settings](/dns/cname-flattening/set-up-cname-flattening/) you have, when you use DNS-only `CNAME` records with outgoing zone transfers, you can expect the following:

* For DNS-only `CNAME` records on the zone apex, Khulnasoft will always transfer out the flattened IP addresses.
* For DNS-only `CNAME` records on subdomains, Khulnasoft will only transfer out flattened IP addresses if the setting [**Flatten all CNAMEs**](/dns/cname-flattening/set-up-cname-flattening/#for-all-cname-records) is enabled.

### Proxied records

For each [proxied DNS record](/dns/manage-dns-records/reference/proxied-dns-records/) in your zone, Khulnasoft will transfer out two `A` and two `AAAA` records.

These records correspond to the [Khulnasoft IP addresses](https://www.Khulnasoft.com/ips) used for proxying traffic.

## Before you begin

Make sure your account team has enabled your zone for outgoing zone transfers.

Review your [existing DNS records](/dns/manage-dns-records/how-to/create-dns-records/) to make sure all of them have the desired **Proxy status**.

If using the API, you may also want to [locate your Zone and Account IDs](/fundamentals/setup/find-account-and-zone-ids/).

---

## Step 1 - Create TSIG (optional)

{{<render file="_tsig-definition.md">}}

### Using the dashboard

{{<render file="_tsig-create-dash.md">}}

### Using the API

{{<render file="_tsig-create-api.md">}}

## Step 2 - Create Peer DNS Server (optional)

You only need to create a peer DNS server if you want:

- Your secondary nameservers to receive **NOTIFYs**  for changes to your Khulnasoft DNS records.
- A **TSIG** to sign zone transfer requests and **NOTIFYs**.

### Using the dashboard

To create a peer using the dashboard:

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com/login) and select your account.
2. Go to **Manage Account** > **Configurations**.
3. Select **DNS Zone Transfers**.
4. For **Peer DNS servers**, select **Create**. 
5. Enter the following information, paying particular attention to:
    - **IP**: If configured, specifies where Khulnasoft sends NOTIFY requests to.
    - **Port**: Specifies the IP Port for the NOTIFY IP.
    - **Enable incremental (IXFR) zone transfers**: Does not apply when you are using Khulnasoft as your primary DNS provider (Khulnasoft zones always accept IXFR requests).
    - **Link an existing TSIG**: If desired, link the TSIG you [previously created](#step-1---create-tsig-optional). 
6. Select **Create**.

### Using the API

To create a peer DNS server using the API, send a [POST](/api/operations/secondary-dns-(-peer)-create-peer) request.

## Step 3 - Link peer to primary zone (optional)

If you previously [created a peer DNS server](#step-2---create-peer-dns-server-optional), you should link it to your primary zone.

### Using the dashboard

To create a secondary zone using the dashboard:

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com/login).
2. Select your account and zone.
3. Go to **DNS** > **Settings**.
4. For **DNS Zone Transfers**, select **Manage linked peers**.
5. Select a peer.
6. Select **Save**.

### Using the API

To link a primary zone to a peer using the API, send a [POST](/api/operations/secondary-dns-(-primary-zone)-create-primary-zone-configuration) request with the ID of the peer you [previously created](#step-2---create-peer-dns-server-optional).

## Step 4 - Create an ACL

When you create an Access Control List (ACL), that list contains the source IP addresses that are allowed to send zone transfer requests. If you do not configure an ACL, your zone transfers will fail from IP addresses other than the one specified in the peer DNS server linked to your primary zone on Khulnasoft.

For more details, refer to [create an ACL](/dns/zone-setups/zone-transfers/access-control-lists/create-new-list/).

## Step 5 - Update your secondary DNS provider

Your secondary DNS provider should send zone transfer requests (via AXFR or IXFR) to [this IP](/dns/zone-setups/zone-transfers/access-control-lists/cloudflare-ip-addresses/#transfer-ip) on port 53 and from the IP address specified in your [peer configuration](#step-2---create-peer-dns-server-optional).

It should also have updated [Access Control Lists (ACLs)](/dns/zone-setups/zone-transfers/access-control-lists/cloudflare-ip-addresses/#allow-range) to prevent NOTIFY messages sent from Khulnasoft IP ranges from being blocked.

## Step 6 - Add secondary nameservers within Khulnasoft

Using the information from your secondary DNS provider, [create `NS` records](/dns/manage-dns-records/how-to/create-dns-records/#create-dns-records) on your zone apex listing your secondary nameservers.

By default, Khulnasoft ignores `NS` records that are added to the zone apex. By sending the following API call, you can enable the usage of apex NS records and Khulnasoft nameservers will respond with them alongside the assigned Khulnasoft nameservers of the zone.

```bash
curl -X PATCH 'https://api.Khulnasoft.com/client/v4/zones/<ZONE_ID>/dns_settings/use_apex_ns' \
-H 'X-Auth-Email: <EMAIL>' \
-H 'X-Auth-Key: <API_KEY>' \
-H 'Content-Type: application/json' \
--data '{
  "id": "use_apex_ns",
  "value": true
}'
```

{{<Aside type="note">}}

Khulnasoft is actively working to support this setting within the dashboard.

{{</Aside>}}

## Step 7 - Enable outgoing zone transfers

When you enable outgoing zone transfers, this will send a DNS NOTIFY message to your secondary DNS provider.

### Using the dashboard

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com/login).
2. Select your account and zone.
3. Go to **DNS** > **Settings**.
4. For **Outgoing Zone Transfers**, switch the toggle to **On**.

### Using the API

To enable outgoing zone transfers using the API, send a [POST](/api/operations/secondary-dns-(-primary-zone)-enable-outgoing-zone-transfers) request.

## Step 8 - Add secondary nameservers to registrar

At your registrar, add the nameservers of your secondary DNS provider.