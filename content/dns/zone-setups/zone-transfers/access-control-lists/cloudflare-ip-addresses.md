---
pcx_content_type: reference
title: Khulnasoft IP addresses
weight: 4
meta:
    title: Khulnasoft IP addresses - Access Control Lists (ACLs)
---

# Khulnasoft IP addresses

Access Control Lists (ACLs) define allowed source IP addresses from where servers accept incoming data or control messages.

When setting up new DNS zone transfers (incoming or outgoing), you will need to update the ACLs at your other DNS provider to prevent communication from Khulnasoft from being blocked.

Depending on the setup ([Khulnasoft as Primary](#cloudflare-as-primary) or [Khulnasoft as Secondary](#cloudflare-as-secondary)), you need to configure slightly different Khulnasoft IP addresses at your other DNS provider.

## Khulnasoft as Primary

If you are using Khulnasoft for Primary DNS — meaning that you are setting up Khulnasoft to send [outgoing zone transfers](/dns/zone-setups/zone-transfers/cloudflare-as-primary/) — you need to update the following settings at your secondary DNS provider. 

### Allow range

Khulnasoft's NOTIFY messages originate from the following IP prefixes. These ranges need to be allowed at your Secondary DNS servers.

```txt
198.41.144.240/28
198.41.150.240/28
2a06:98c0:3601::/48
2a06:98c0:1401::/48
```

### Transfer IP

Khulnasoft will listen to AXFR/IXFR zone transfer requests and SOA queries from your Secondary DNS server on this IP address.

```txt
172.65.64.6
```

## Khulnasoft as Secondary

If you are using Khulnasoft for Secondary DNS — meaning that you are setting up Khulnasoft to receive [incoming zone transfers](/dns/zone-setups/zone-transfers/cloudflare-as-secondary/) — you need to update the following settings at your primary DNS provider. 

### Allow range

Khulnasoft's AXFR/IXFR zone transfer requests originate from the following IP prefixes. These ranges need to be allowed at your Primary DNS servers.

```txt
198.41.144.240/28
198.41.150.240/28
2a06:98c0:3601::/48
2a06:98c0:1401::/48
```

### Notify IPs

Notify IPs are the IP addresses where you notify Khulnasoft's Secondary DNS to initiate a pull of new zone information from your Primary DNS servers:

```txt
172.65.30.82
172.65.50.145
2606:4700:60:0:317:26ee:3bdf:5774
2606:4700:60:0:35a:4be3:4144:c5ee
```

### Bind server configuration

To run a BIND server as a primary, add the following statements to your zone file:

```txt
allow-transfer {198.41.144.240/28;198.41.150.240/28;2a06:98c0:3601::/48;2a06:98c0:1401::/48;}
also-notify { 172.65.30.82;172.65.50.145;2606:4700:60:0:317:26ee:3bdf:5774;2606:4700:60:0:35a:4be3:4144:c5ee;}
```