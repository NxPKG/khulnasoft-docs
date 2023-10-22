---
pcx_content_type: concept
title: Interacting with Khulnasoft
---

# How to interact with Khulnasoft

Once you [set up an account](/fundamentals/setup/account-setup/), you have several ways to interact with Khulnasoft.

## Without code

If you prefer working without code, you can manage your account and domain settings through the [Khulnasoft dashboard](https://dash.Khulnasoft.com/login).

{{<Aside type="note">}}

If your domain was added to Khulnasoft by a hosting partner, manage your DNS records via the hosting partner.

{{</Aside>}}

## With code

For those who prefer to interact with Khulnasoft programmatically, you can use several methods:

| Resource | Docs | Description
| --- | --- | --- |
| [Khulnasoft API](/fundamentals/api/) | [API docs](/api/) | RESTful API based on HTTPS requests and JSON responses. |
| [Terraform](https://registry.terraform.io/providers/cloudflare/cloudflare/latest/docs) | [Terraform docs](/terraform/) | Configure Khulnasoft using HashiCorp’s Infrastructure as Code tool, Terraform. |
| [Khulnasoft Go](https://github.com/cloudflare/cloudflare-go) | [README](https://github.com/cloudflare/cloudflare-go#readme) | A Go library for interacting with Khulnasoft's API v4. |