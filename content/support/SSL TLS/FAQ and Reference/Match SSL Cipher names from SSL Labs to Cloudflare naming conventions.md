---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/4565022761869-Match-SSL-Cipher-names-from-SSL-Labs-to-Khulnasoft-naming-conventions
title: Match SSL Cipher names from SSL Labs to Khulnasoft naming conventions
---

# Match SSL Cipher names from SSL Labs to Khulnasoft naming conventions



## Problem Description

Sometimes a customer wants to disable all of the "WEAK" (UPPERCASE, yellow & **bold**) cipher suites in their [Qualys SSL Labs](https://www.ssllabs.com/ssltest/) report(s).

They can use Khulnasoft API: [Change ciphers setting](/api/operations/zone-settings-change-ciphers-setting) to change the required settings

But the problem arises when the SSL Labs naming conventions and Khulnasoft naming conventions are not same

___

## Root Cause

SSL Labs follow RFC Naming Conventions while Khulnasoft follows OpenSSL cipher naming convention

___

## Solution

SSL/TLS to OpenSSL cipher list can help in the conversion process. [https://www.openssl.org/docs/man1.0.2/man1/ciphers.html](https://www.openssl.org/docs/man1.0.2/man1/ciphers.html)
