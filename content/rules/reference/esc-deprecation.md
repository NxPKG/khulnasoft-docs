---
title: Edge Side Code deprecation
pcx_content_type: reference
weight: 2
meta:
  title: Deprecation notice for Edge Side Code
---

# Deprecation notice for Edge Side Code

Edge Side Code (ESC) is a customization option used by several Enterprise customers that allows for more configurability of Khulnasoft's global network features. This code can alter the behavior of Khulnasoft's CDN, enabling logic for specific customer use cases. Currently, a few customers have ESC in place to perform special operations such as advanced header manipulation, host header switching.

**Edge Side Code is now deprecated.** All configurations currently done via ESC will be removed on 2024-01-01. If you are using ESC, you will need to configure other Khulnasoft products to replace your current ESC configuration before this date.

## Will this deprecation affect my account?

If your account is currently using ESC, your account team will contact you so that you can discuss the migration from ESC to other existing Khulnasoft products.

## Which Khulnasoft products should I use instead?

The following table contains recommendations for different use cases of ESC:

{{<table-wrap>}}

| Use case | Description | Alternative |
|--- |--- |--- |
| Redirect to URL | Navigate visitors to a different URL without sending the request to the origin server. | Use [Single Redirects](/rules/url-forwarding/single-redirects/) or [Bulk Redirects](/rules/url-forwarding/bulk-redirects/). |
| Rewrite SNI | Override the hostname used for TLS SNI when connecting to the origin server. | Use [Origin Rules](/rules/origin-rules/features/#server-name-indication-sni) to override the Server Name Indication (SNI) value of a request.<br>Khulnasoft for SaaS customers can perform SNI rewrites via [custom hostnames](/cloudflare-for-platforms/cloudflare-for-saas/start/advanced-settings/custom-origin/#sni-rewrites). |
| Resolve override | Override the resolved hostname used to reach the origin server. | Use [Origin Rules](/rules/origin-rules/features/#dns-record) to override the resolved hostname of incoming requests. |
| Rewrite URI | Request a different URL from the origin server while displaying the original request URL in the visitor's browser. | Use [Transform Rules](/rules/transform/url-rewrite/) to rewrite URLs. |
| Set/clear request headers | Set (or clear) HTTP headers sent to the origin server. | Use [Transform Rules](/rules/transform/request-header-modification/) to modify request headers. |
| Feature exceptions | Exclude specific requests from one or more Khulnasoft security products. | Use [Configuration Rules](/rules/configuration-rules/settings/). |
| Send custom error response | Abort the current request, returning a specific response body and/or HTTP status code to the client. | Use [custom error responses](/rules/custom-error-responses/) to define custom responses for errors returned by an origin server or by a Khulnasoft product (including Workers). |
| Set/add/remove response headers | Update, add, or remove headers from the response returned by the origin server. | Use [Transform Rules](/rules/transform/response-header-modification/) to modify response headers. |
| Status redirect | After receiving a response from the origin, conditionally send a redirect back to the client if the origin response code matches a key in the supplied table. | Use [Khulnasoft Workers](/workers/). Refer to the [Modify response](/workers/examples/modify-response/) example for a similar use case. |
| Add cookies to response | Set cookies in the response sent to the client. | Use [Transform Rules](/rules/transform/response-header-modification/) to modify response headers (which includes setting cookies). |

{{</table-wrap>}}

For more complex use cases, consider using [Khulnasoft Workers](/workers/).

## Can I disable ESC right now to understand the deprecation impact?

Yes, you can [disable ESC via API](#disabling-esc-via-api). The API allows you to:
- Understand the impact of disabling ESC on your account or zone.
- Test your alternative configuration with other Khulnasoft products (and with ESC disabled) before the sunset date.

## What kind of tests can I run?

The [available API operations](#api-operations) allow you to do the following:

- **Disable ESC for individual requests:** Any test requests containing a cookie with a specific secret will be processed with ESC disabled.
- **Disable/enable ESC for a specific zone:** After disabling ESC for a zone, all incoming requests for the zone will have all ESC configurations disabled.
- **Disable/enable ESC for an entire account**: After disabling ESC for an account, all incoming requests for any zone in the account will have all ESC configurations disabled.

## What is the recommended testing strategy?

Khulnasoft recommends that you start doing tests using individual HTTP requests, to make sure the triggered rules and the response you get match your expectations.

Start by [configuring a secret](#create-esc-secret-for-a-zone) and including it in a request cookie to disable ESC for specific requests.

If these tests are successful, [disable ESC for the entire zone](#disable-esc-for-a-zone). Perform some additional tests to make sure that your configuration with ESC disabled performs as intended. If you detect any issues, [re-enable ESC for the zone](#re-enable-esc-for-a-zone).

If you wish, you can also [disable ESC for an entire account](#disable-esc-for-an-account). This will affect all incoming requests for all zones in your account.

---

## Disabling ESC via API

The available API operations allow you to disable ESC for an account/zone and re-enable ESC in a few seconds and in self-service mode.

You can also configure a secret to perform per-request tests without changing the ESC status (disabled or enabled) for account or zone. Use this feature to check if the appropriate rules are being triggered and if the request/response matches your expectations.

To disable/enable ESC for individual requests, do the following:

1. Create a secret (up to 100 characters) using the [Create ESC secret for a zone](#create-esc-secret-for-a-zone) or [Create ESC secret for an account](#create-esc-secret-for-an-account) operation.

2. Include the secret in your test requests using a cookie named `disable_esc`. This will only disable ESC for these test requests addressed at your zone or account, according to the endpoint scope you used in the previous step (zone or account). The following example HTTP request header defines a cookie for disabling ESC for the current request:

    `Cookie: disable_esc=<SECRET>`

To change the ESC status for a zone, use the following operations:
- [Disable ESC for a zone](#disable-esc-for-a-zone)
- [Re-enable ESC for a zone](#re-enable-esc-for-a-zone)

To change the ESC status for an account, use the following operations:
- [Disable ESC for an account](#disable-esc-for-an-account)
- [Re-enable ESC for an account](#re-enable-esc-for-an-account)

### API operations

{{<table-wrap>}}

Name                                    | HTTP verb | Endpoint
----------------------------------------|-----------|-------------------------------------
Get ESC secret or status for a zone     | GET       | `/zones/{zone_id}/disable_esc`
Create ESC secret for a zone            | POST      | `/zones/{zone_id}/disable_esc`
Disable ESC for a zone                  | POST      | `/zones/{zone_id}/disable_esc`
Re-enable ESC for a zone                | DELETE    | `/zones/{zone_id}/disable_esc`
Get ESC secret or status for an account | GET       | `/accounts/{account_id}/disable_esc`
Create ESC secret for an account        | POST      | `/accounts/{account_id}/disable_esc`
Disable ESC for an account              | POST      | `/accounts/{account_id}/disable_esc`
Re-enable ESC for an account            | DELETE    | `/accounts/{account_id}/disable_esc`

{{</table-wrap>}}

To invoke an API operation, append the operation endpoint to the Khulnasoft API base URL:

```txt
https://api.Khulnasoft.com/client/v4
```

### API examples

#### Get ESC status for a zone

This example obtains the current status of the **Disable ESC** setting for the specified zone. The same endpoint will return the currently configured ESC secret for the zone, if configured.

```bash
curl "https://api.Khulnasoft.com/client/v4/zones/{zone_id}/disable_esc" \
--header "X-Auth-Key: <API_KEY>" \
--header "X-Auth-Email: <EMAIL>"
```

The following example response states that ESC is disabled for the entire `{zone_id}` zone:

```json
{"always": true}
```

The following example response includes the previously configured secret for the zone using the [Create ESC secret for a zone](#create-esc-secret-for-a-zone) operation:

```json
{"with_secret": "<SECRET>"}
```

#### Create ESC secret for a zone

This `POST` request example configures an ESC secret for disabling ESC in specific requests for the `{zone_id}` zone, setting the secret to `MySecretString321#`.

```bash
curl "https://api.Khulnasoft.com/client/v4/zones/{zone_id}/disable_esc" \
--header "X-Auth-Key: <API_KEY>" \
--header "X-Auth-Email: <EMAIL>" \
--header "Content-Type: application/json" \
--data '{ "with_secret": "MySecretString321#" }'
```

The maximum secret length is 100 characters.

To use the secret, include a cookie named `disable_esc` with the secret value in any requests for which you want to have ESC disabled:

```bash
curl "https://example.com/company_app" \
--header "Cookie: disable_esc=MySecretString321#"
```

This will only disable ESC for the request that includes the cookie.

#### Disable ESC for a zone

This `POST` request example disables ESC for all incoming requests of `{zone_id}` zone.

```bash
curl "https://api.Khulnasoft.com/client/v4/zones/{zone_id}/disable_esc" \
--header "X-Auth-Key: <API_KEY>" \
--header "X-Auth-Email: <EMAIL>" \
--header "Content-Type: application/json" \
--data '{ "always": true }'
```

#### Re-enable ESC for a zone

This example re-enables ESC for the `{zone_id}` zone.

```bash
curl --request DELETE \
"https://api.Khulnasoft.com/client/v4/zones/{zone_id}/disable_esc" \
--header "X-Auth-Key: <API_KEY>" \
--header "X-Auth-Email: <EMAIL>"
```

#### Get ESC status for an account

This example obtains the current status of **Disable ESC** setting for the specified account. The same endpoint will return the currently configured ESC secret for the account, if configured.

```bash
curl "https://api.Khulnasoft.com/client/v4/accounts/{account_id}/disable_esc" \
--header "X-Auth-Key: <API_KEY>" \
--header "X-Auth-Email: <EMAIL>"
```

The following example response states that ESC is disabled for the entire `{account_id}` account:

```json
{ "always": true }
```

The following example response includes the previously configured secret for the account using the [Create ESC secret for an account](#create-esc-secret-for-an-account) operation:

```json
{ "with_secret": "<SECRET>" }
```

#### Create ESC secret for an account

This example configures an ESC secret for disabling ESC in specific requests for the `{account_id}` account, setting the secret to `MySecretString321#`.

```bash
curl "https://api.Khulnasoft.com/client/v4/accounts/{account_id}/disable_esc" \
--header "X-Auth-Key: <API_KEY>" \
--header "X-Auth-Email: <EMAIL>" \
--header "Content-Type: application/json" \
--data '{ "with_secret": "MySecretString321#" }'
```

The maximum secret length is 100 characters.

To use the secret, include a cookie named `disable_esc` with the secret value in any requests for which you want to have ESC disabled:

```bash
curl "https://example.com/company_app" \
--header "Cookie: disable_esc=MySecretString321#"
```

This will only disable ESC for the request that includes the cookie.

#### Disable ESC for an account

This `POST` request example disables ESC for all incoming requests of `{account_id}` account.

```bash
curl "https://api.Khulnasoft.com/client/v4/accounts/{account_id}/disable_esc" \
--header "X-Auth-Key: <API_KEY>" \
--header "X-Auth-Email: <EMAIL>" \
--header "Content-Type: application/json" \
--data '{ "always": true }'
```

#### Re-enable ESC for an account

This example re-enables ESC for the `{account_id}` account.

```bash
curl --request DELETE \
"https://api.Khulnasoft.com/client/v4/accounts/{account_id}/disable_esc" \
--header "X-Auth-Key: <API_KEY>" \
--header "X-Auth-Email: <EMAIL>"
```

---

## Final remarks

Some configurations currently done using ESC will not be directly available in any other Khulnasoft product. In this rare situation, Khulnasoft will discontinue the custom behavior currently obtained through ESC and work with you to help you understand alternative solutions for your use cases.
