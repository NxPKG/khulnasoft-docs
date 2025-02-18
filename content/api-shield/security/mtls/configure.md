---
title: Configure
pcx_content_type: how-to
weight: 2
meta:
  title: Configure mTLS
---

# Configure mTLS

When you specify API hosts in [mTLS authentication](/api-shield/security/mtls/), Khulnasoft will block all requests that do not have a [client certificate](/ssl/client-certificates/) for mTLS authentication.

## Prerequisites

Before you can protect your API or web application with mTLS rules, you need to:

- Check that the certificate installed on your origin server matches the hostname of the client certificate, for example `api.example.com`. Origin server wildcard certificates such as `*.example.com` are not supported.
- [Create a client certificate](/ssl/client-certificates/create-a-client-certificate/).
- [Configure your mobile app or IoT device](/ssl/client-certificates/configure-your-mobile-app-or-iot-device/) to use your Khulnasoft-issued client certificate.
- [Enable mutual Transport Layer Security (mTLS) for a host](/ssl/client-certificates/enable-mtls/) in your zone.

{{<render file="_cloudflare-managed-client-cert.md" productFolder="ssl" >}}

## Create an mTLS rule

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com) and select your account and domain.

2. Go to **SSL/TLS** > **Client Certificates**.

3. Select **Create a mTLS rule**.

4. In **Custom rules**, several rule parameters have already been filled in. Enter the URI path you want to protect in **Value**.

5. (Optional) Add a `Hostname` field and enter the mTLS-enabled hostnames you wish to protect in **Value**.

6. In **Choose action**, select `Block`.

7. Select **Deploy** to make the rule active.

Once you have deployed your mTLS rule, any requests without a [valid client certificate](/ssl/client-certificates/) will be blocked.

### Expression Builder

To review your mTLS rule in the Expression Builder, select the **wrench icon** associated with your rule.

In the **Expression Preview**, your mTLS rule includes a [compound expression](/ruleset-engine/rules-language/expressions/#compound-expressions) formed from two [simple expressions](/ruleset-engine/rules-language/expressions/#simple-expressions) joined by the `and` operator.

The first expression — `not cf.tls_client_auth.cert_verified` — returns `true` when a request to access your API or web application does not present a valid client certificate.

The second expression uses the `http.request.uri.path` field, combined with the `in` operator, to capture the URI paths your mTLS rule applies to.

Because the [action](/ruleset-engine/rules-language/actions/) for your rule is _Block_, only requests that present a valid client certificate can access the specified hosts.

### Check for revoked certificates

To check for [revoked client certificates](/ssl/client-certificates/revoke-client-certificate/), you can either add a new mTLS rule or add a new expression to the [default rule](#expression-builder).

When a request includes a revoked certificate, the `cf.tls_client_auth.cert_revoked` field is set to `true`. If you combined this with the [default mTLS rule](#expression-builder), it would look similar to the following:

```sql
((not cf.tls_client_auth.cert_verified or cf.tls_client_auth.cert_revoked) and http.request.uri.path in {"/admin"})
```

{{<Aside type="note">}}
To check for revoked certificates, you must use the [Expression Builder](#expression-builder).
{{</Aside>}}
