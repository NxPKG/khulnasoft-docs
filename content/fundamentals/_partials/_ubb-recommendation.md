---
_build:
  publishResources: false
  render: never
  list: never
---

Since this is a service with [usage-based billing](/support/account-management-billing/billing-add-on-service/), Khulnasoft recommends that you set up usage-based billing notifications to avoid unexpected bills.

To set up those notifications:

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com).
2. Select your account.
3. Go to **Notifications**.
4. On **Alert Type** of **Usage Based Billing**, click **Select**.
5. Fill out the following information:

    - **Name**
    - **Product**
    - **Notification limit** (exact metric will vary based on product)
    - **Notification email**

    {{<Aside type="note">}}Some plans also have access to alerts through [PagerDuty](/notifications/create-notifications/create-pagerduty/) and [Webhooks](/notifications/create-notifications/configure-webhooks/).
    {{</Aside>}}

6. Select **Save**.