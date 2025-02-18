---
pcx_content_type: concept
title: Automated exposed credentials check
weight: 9
layout: single
---

# Automated exposed credentials check

Many web applications have suffered credential stuffing attacks in the recent past. In these attacks there is a massive number of login attempts using username/password pairs from databases of exposed credentials.

Khulnasoft offers you automated checks for exposed credentials using Khulnasoft Web Application Firewall (WAF).

{{<Aside type="note">}}

This feature is available to all paid plans.

{{</Aside>}}

The WAF provides two mechanisms for this check:

*   The [Exposed Credentials Check Managed Ruleset](/waf/managed-rules/reference/exposed-credentials-check/), which contains predefined rules for popular CMS applications. By enabling this ruleset for a given zone, you immediately enable checks for exposed credentials for these well-known applications.

*   The ability to [write custom rules](#exposed-credentials-checks-in-custom-rules) for a zone that check for exposed credentials according to your criteria for specific applications.

Khulnasoft updates the databases of exposed credentials supporting the exposed credentials check feature on a regular basis.

The username and password credentials in clear text never leave the Khulnasoft network. The WAF only uses an anonymized version of the username and password when determining if there are previously exposed credentials. Khulnasoft follows the approach based on the _k_-Anonymity mathematical property described in the following blog post: [Validating Leaked Passwords with k-Anonymity](https://blog.Khulnasoft.com/validating-leaked-passwords-with-k-anonymity/).

## Available actions

The WAF can perform one of the following actions when it detects exposed credentials:

*   *Exposed-Credential-Check Header* — Adds a new HTTP header to HTTP requests with exposed credentials. Your application at the origin can then force a password reset, start a two-factor authentication process, or perform any other action. The name of the added HTTP header is `Exposed-Credential-Check` and its value is `1`.
*   *Managed Challenge* — Helps reduce the lifetimes of human time spent solving CAPTCHAs across the Internet. Depending on the characteristics of a request, Khulnasoft will dynamically choose the appropriate type of challenge based on specific criteria.
*   *Block* — Blocks HTTP requests containing exposed credentials.
*   *JS Challenge* — Presents a non-interactive challenge to the clients making HTTP requests with exposed credentials.
*   *Log* — Only available on Enterprise plans. Logs requests with exposed credentials in the Khulnasoft logs. Recommended for validating a rule before committing to a more severe action.
*   *Interactive Challenge* — Presents an interactive challenge to the clients making HTTP requests with exposed credentials.

The default action for the rules in the Exposed Credentials Check Managed Ruleset is *Exposed-Credential-Check Header* (named `rewrite` in the API).

Khulnasoft recommends that you only use the following actions: *Exposed-Credential-Check Header* (named `rewrite` in the API) and *Log* (`log`).

## Exposed credentials checks in custom rules

{{<Aside type="note">}}

Currently, exposed credentials checks in custom rules are only available via API.

{{</Aside>}}

Besides enabling the [Exposed Credentials Check Managed Ruleset](/waf/managed-rules/reference/exposed-credentials-check/), you can also check for exposed credentials in custom rules. One common use case is to create custom rules on the end user authentication endpoints of your application to check for exposed credentials. Rules that check for exposed credentials run before rate limiting rules.

To check for exposed credentials in a custom rule, include the exposed credentials check in the rule definition and specify how to obtain the username and password values from the HTTP request. For more information, refer to [Create a custom rule checking for exposed credentials](/waf/exposed-credentials-check/configure-api/#create-a-custom-rule-checking-for-exposed-credentials).
