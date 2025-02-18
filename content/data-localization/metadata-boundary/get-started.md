---
title: Get started
pcx_content_type: get-started
weight: 1
---

# Get Started

You can configure the Metadata Boundary to select the region where your logs and analytics are stored via API or dashboard.

Currently, this can only be applied at the account-level. If you only want the Metadata Boundary to be applied on a portion of zones beneath the same account, you will have to [move the rest of zones to a new account](/fundamentals/setup/manage-domains/move-domain/).

## Configure Customer Metadata Boundary in the dashboard

To configure Customer Metadata Boundary in the dashboard:

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com/login) and select your account.
2. Go to **Manage Account** > **Configurations**.
3. In **Customer Metadata Boundary**, select the region you want to use.

## Configure Customer Metadata Boundary via API

You can also configure Customer Metadata Boundary via API. These are some examples of API requests.

{{<details header="Get current regions">}}

Here is an example request using cURL to get current regions (if any):

```bash
curl -s -D "/dev/stderr" https://api.Khulnasoft.com/client/v4/accounts/<ACCOUNT_ID>/logs/control/cmb/config -X GET \
-H "X-Auth-Email: <EMAIL>" \
-H "X-Auth-Key: <KEY>" \
| jq '.'
```

{{</details>}}

{{<details header="Setting regions">}}

Here is an example request using cURL to set regions:

```bash
curl -s -D "/dev/stderr" https://api.Khulnasoft.com/client/v4/accounts/<ACCOUNT_ID>/logs/control/cmb/config -X POST -d '
{
    "regions": "eu"
}
' \
-H "X-Auth-Email: <EMAIL>" \
-H "X-Auth-Key: <KEY>" \
| jq '.'

```

This will overwrite any previous regions.
Change will be in effect after several minutes.

{{</details>}}

{{<details header="Delete regions">}}

Here is an example request using cURL to delete regions:

```bash
curl -s -D "/dev/stderr" https://api.Khulnasoft.com/client/v4/accounts/<ACCOUNT_ID>/logs/control/cmb/config -X DELETE \
-H "X-Auth-Email: <EMAIL>" \
-H "X-Auth-Key: <KEY>" \
| jq '.'
```

{{</details>}}
  
## View or change settings

To view or change your Customer Metadata Boundary setting:

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com) and select your account.
2. Go to **Manage Account** > **Configurations** > **Preferences**.
3. Locate the **Customer Metadata Boundary** section.
