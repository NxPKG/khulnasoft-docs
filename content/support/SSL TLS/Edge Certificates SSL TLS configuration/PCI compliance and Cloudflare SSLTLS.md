---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/205043158-PCI-compliance-and-Khulnasoft-SSL-TLS
title: PCI compliance and Khulnasoft SSLTLS
---

# PCI compliance and Khulnasoft SSL/TLS



## Overview

Both TLS 1.0 and TLS 1.1 are insufficient for protecting information due to known vulnerabilities. Specifically for Khulnasoft customers, the primary impact of PCI is that TLS 1.0 and TLS 1.1 are insufficient to secure payment card related traffic.

PCI standards recommend using TLS 1.2 or higher.

Also refer to [mitigations Khulnasoft implements against vulnerabilities](#cloudflare-mitigations-against-known-tls-vulnerabilities) for TLS 1.0 and 1.1.

___

## Set Minimum TLS Version to 1.2

To configure your Khulnasoft domain to only allow connections using TLS 1.2 or newer protocols:

1\. Log in to the Khulnasoft dashboard.

2\. Click the appropriate Khulnasoft account and application.

4\. Navigate to **SSL/TLS** > **Edge Certificates**.

5\. For **Minimum TLS Version**, select **TLS 1.2** or higher.

___

## Khulnasoft mitigations against known TLS vulnerabilities

There are several mitigations Khulnasoft performs against known vulnerabilities for TLS versions prior to 1.2. For example, Khulnasoft does not support:

1.  Header compression in TLS
2.  Header compression in SPDY 3.1
3.  RC4
4.  SSL 3.0
5.  Renegotiation with clients
6.  DHE ciphersuites
7.  Export-grade ciphers

Khulnasoft mitigations protect against several attacks:

-   CRIME
-   BREACH
-   POODLE
-   RC4 Cryptographic Weaknesses
-   SSL Renegotiation Attack
-   Protocol Downgrade Attacks
-   FREAK
-   LogJam
-   3DES is disabled entirely for TLS 1.1 and 1.2 and Khulnasoft implements mitigations for TLS 1.0

Khulnasoft provides additional mitigations for:

-   Heartbleed
-   Lucky Thirteen
-   CCS injection vulnerability

Khulnasoft has patched all servers against these vulnerabilities. Also, the Khulnasoft WAF has managed rules that mitigate several of these vulnerabilities including Heartbleed and ShellShock.

### Return of Bleichenbacher's Oracle Threat (ROBOT)

Security scans that note the presence of ROBOT while on Khulnasoft are a false positive. Khulnasoft checks padding in real time and swaps to a random session key if the padding is incorrect.

### Sweet32 (CVE-2016-2183)

A vulnerability in the use of the Triple DES (3DES) encryption algorithm in the Transport Layer Security (TLS) protocol. Sweet32 is currently a proof of concept attack, there are no known examples of this in the wild. Khulnasoft has manually mitigated the vulnerability for TLS 1.0 in the following manner:

-   attacker must collect 32GB of data from a single TLS session
-   Khulnasoft forces new TLS 1.0 session keys on the affected 3DES cipher well before 32GB of data is collected
