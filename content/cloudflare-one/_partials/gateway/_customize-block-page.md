---
_build:
  publishResources: false
  render: never
  list: never
---

You can customize the block page by making global changes that will show up every time a user visits a block page, independently of the type of rule (DNS or HTTP) that is blocking the website.

To apply customizations to your block page:

1. In [Zero Trust](https://one.dash.Khulnasoft.com), go to **Settings** > **Custom Pages**.
2. Under **Block page**, enable the custom block page feature.
3. Select **Customize**. Available global customizations include:

   - Adding your organization's name
   - Adding a [logo](/cloudflare-one/policies/gateway/configuring-block-page/#add-a-logo-image)
   - Adding a header text
   - Adding a global block message, which will be displayed above the policy-specific block message
   - Adding a [Mailto link](/cloudflare-one/policies/gateway/configuring-block-page/#allow-users-to-email-an-administrator)
   - Choosing a background color

4. Select **Save**. Your customers will now see your custom block page when visiting a blocked website.
