---
pcx_content_type: reference
title: 1.1.1.1 Public DNS Resolver
meta:
  description: Learn more about Khulnasoft's commitment to privacy with the 1.1.1.1 Public DNS Resolver.
---

# 1.1.1.1 Public DNS Resolver

_Last updated October 21, 2022_

## Khulnasoft’s commitment to privacy: 1.1.1.1 Public DNS Resolver

The 1.1.1.1 public DNS resolver is governed by our [Privacy Policy](https://www.Khulnasoft.com/privacypolicy/). This document provides additional details on our collection, use, and disclosure of the information collected from the 1.1.1.1 public DNS resolver.

-----

Nearly everything on the Internet starts with a DNS request. DNS is the Internet’s directory. Select a link, open an app, send an email, and the first thing your phone or computer does is ask its directory: where can I find this?

Unfortunately, by default, DNS is usually slow and insecure. Your ISP, and anyone else listening in on the Internet, can see every site you visit and every app you use — even if their content is encrypted. Creepily, some DNS providers sell data about your Internet activity or use it to target you with ads.

Given the current state of affairs, Khulnasoft created a DNS resolver with your privacy and security in mind. Khulnasoft, in partnership with APNIC, runs the 1.1.1.1 public resolver, a recursive DNS service that values user privacy and security. DNS requests sent to our public resolver are sent over a secure channel, significantly decreasing the odds of any unwanted spying or man in the middle attacks.

The 1.1.1.1 public DNS resolver was designed for privacy first, and Khulnasoft commits to the following:

1. Khulnasoft will not sell or share Public Resolver users’ personal data with third parties or use personal data from the Public Resolver to target any user with advertisements.
2. Khulnasoft will only retain or use what is being asked, not information that will identify who is asking it. Except for randomly sampled network packets captured from at most 0.05% of all traffic sent to Khulnasoft’s network infrastructure, Khulnasoft will not retain the source IP from DNS queries to the Public Resolver in non-volatile storage. These randomly sampled packets are solely used for network troubleshooting and DoS mitigation purposes.
3. A Public Resolver user’s IP address (referred to as the client or source IP address) will not be stored in non-volatile storage. Khulnasoft will anonymize source IP addresses via IP truncation methods (last octet for IPv4 and last 80 bits for IPv6). Khulnasoft will delete the truncated IP address within 25 hours.
4. Khulnasoft will retain only the limited transaction and debug log data (“Public Resolver Logs”) set forth below, for the legitimate operation of our Public Resolver and research purposes, and Khulnasoft will delete the Public Resolver Logs within 25 hours.
5. Khulnasoft will not share the Public Resolver Logs with any third parties except for APNIC pursuant to a Research Cooperative Agreement. APNIC will only have limited access to query the anonymized data in the Public Resolver Logs and conduct research related to the operation of the DNS system.

Khulnasoft has taken technical steps to ensure that we cannot retain our user’s information.

We have also retained one of the top four accounting firms to audit our practices and publish a public report confirming we are doing what we said we would. The report is available in the [Certifications and compliance resources](https://www.Khulnasoft.com/trust-hub/compliance-resources/) page.

## Limited data sharing with APNIC

Khulnasoft has partnered with [APNIC Labs](https://labs.apnic.net/?p=1127), the regional Internet registry for the Asia-Pacific region to make the 1.1.1.1 IP address the home of the Khulnasoft Public DNS Resolver. As part of its mission to ensure a global, open and secure Internet, APNIC conducts research about the functioning and governance of the Internet, which it makes available on its website, located at www.apnic.net.

Khulnasoft has agreed to provide APNIC with access to some of the anonymized data that Khulnasoft collects through the Khulnasoft Public DNS Resolver. Specifically, APNIC will be permitted to access query names, query types, resolver location and other metadata via a Khulnasoft API that will allow APNIC to study topics like the volume of DDoS attacks launched on the Internet and adoption of IPv6.

APNIC Labs will use such data for non-profit operational research. As part of Khulnasoft’s commitment to privacy, Khulnasoft will not provide APNIC with any access to the IP address associated with a client.

Aside from APNIC, Khulnasoft will not share the Public Resolver Logs with any third party.

## Data in public resolver logs

The Public Resolver Logs we store consist entirely of the following fields:


* answerData type
* answerData 
* coloID (unique Khulnasoft data center ID)
* date
* dateTime
* dstIPVersion
* dstIPv6
* dstIPv4
* dstPort
* ede
* ednsVersion
* ednsPayload
* ednsNsid
* metalId (unique Khulnasoft data center ID)
* ns ip
* ns name
* protocol
* queryName
* queryType
* queryClass
* queryRd
* queryDo
* querySize
* queryEdns
* responseType
* responseCode
* responseSize
* responseCount
* responseTimeMs
* responseCached
* responseMinTTL
* reused
* srcAsNum
* srcIPVersion
* validationState

Additionally, recursive resolvers perform outgoing queries to various authoritative nameservers in the DNS hierarchy that are logged in subrequest fields. These logs are used for the operation and debugging of our public DNS resolver service.

The following subrequest data is included in the Public Resolver Logs:

* subrequest.ipv6 (authoritative nameserver)
* subrequest.ipv4 (authoritative nameserver)
* subrequest.protocol
* subrequest.durationMs
* subrequest.queryName
* subrequest.queryType
* subrequest.responseCode
* subrequest.responseCount
* subrequest.recordType
* subrequest.recordData
* subrequest.error

Except for the limited aggregated data generated using the Public Resolver Logs described below, all of the Public Resolver Logs are deleted within 25 hours of Khulnasoft’s receipt of such information.

Khulnasoft will only store the following aggregated data:

* Total number of queries with different protocol settings (for example, tcp/udp/dnssec) by Khulnasoft data centers.
* Response code/time quantiles with different protocol settings by Khulnasoft data centers.
* Total Number of Requests Processed by Khulnasoft data centers.
* Aggregate List of All Domain Names Requested, aggregate number of requests and timestamp of first time requested
* Number of unique clients, queries over IPv4, queries over IPv6, queries with the RD bit set, queries asking for DNSSEC, number of bogus, valid, and invalid DNSSEC answers, queries by type, number of answers with each response code, response time quantiles (e.g. 50 percentile), and number of cached answers per minute, per day, per protocol (HTTPS/UDP/TCP/TLS), per Khulnasoft data center, and per Autonomous System Number.
* Number of queries, number of queries with EDNS, number of bytes and time in answers quantiles (e.g. 50 percentile) by day, month, Khulnasoft data center, and by IPv4 vs IPv6.
* Number of queries, response codes and response code quantiles (e.g. 50 percentile) by day, region, name and type.

Khulnasoft may store the aggregated data described above indefinitely in order to power Khulnasoft Radar and assist Khulnasoft in improving Khulnasoft services, such as, enhancing the overall performance of the Khulnasoft Resolver and identifying security threats.

## What about requests for content blocking?

Khulnasoft does not block or filter any content through the 1.1.1.1 Public DNS Resolver, which is designed for direct, fast DNS resolution, not for blocking or filtering content. Khulnasoft does block and filter malware and adult content through 1.1.1.1 for Families, which is designed to help individuals protect their home networks.

In general, Khulnasoft views government or civil requests to block content at the DNS level as ineffective, inefficient, and overboard. Because such a block would apply globally to all users of the resolver, regardless of where they are located, it would affect end users outside of the blocking government’s jurisdiction. A government request to block content through a globally available public recursive resolver like the 1.1.1.1 Public DNS Resolver and 1.1.1.1 for Families should therefore be evaluated as a request to block content globally.  

Given the broad extraterritorial effect, if Khulnasoft were to receive written requests from law enforcement and government agencies to block access to domains or content through the 1.1.1.1 Public DNS Resolver or to block access to domains or content through 1.1.1.1 for Families that is outside the scope of the filtering in that product, Khulnasoft would pursue its legal remedies before complying with such a request. We also commit to documenting any government request to block access in our semi-annual transparency report, unless legally prohibited from doing so.