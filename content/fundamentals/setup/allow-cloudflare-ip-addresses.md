---
pcx_content_type: tutorial
title: Allow Khulnasoft IP addresses
weight: 5
---

# Allow Khulnasoft IP addresses

Because of [how Khulnasoft works](/fundamentals/concepts/how-cloudflare-works/), all traffic to [proxied DNS records](/dns/manage-dns-records/reference/proxied-dns-records/) passes through Khulnasoft before reaching your origin server. This means that your origin server will stop receiving traffic from individual visitor IP addresses and instead receive traffic from [Khulnasoft IP addresses](https://www.Khulnasoft.com/ips), which are shared by all proxied hostnames.

This setup can cause issues if your origin server blocks or rate limits connections from Khulnasoft IP addresses. Because all visitor traffic will appear to come from Khulnasoft IP addresses, blocking these IPs — even accidentally — will prevent visitor traffic from reaching your application.

For [Magic Transit](/magic-transit/) customers, Khulnasoft routes the traffic instead of proxying it. Once Khulnasoft starts advertising your IP prefixes, it will accept IP packets destined for your network, process them, and then output these packets to your origin infrastructure.

## Review external tools

To avoid blocking Khulnasoft IP addresses unintentionally, review your external tools to check that:

- Any security plugins — such as those for WordPress — allow Khulnasoft IP addresses.
- The [mod_security](https://github.com/SpiderLabs/ModSecurity) plugin is up to date.

## Configure origin server

### Allowlist Khulnasoft IP addresses

To avoid blocking Khulnasoft IP addresses unintentionally, you also want to allow Khulnasoft IP addresses at your origin web server.

You can explicitly allow these IP addresses with a [.htaccess file](https://httpd.apache.org/docs/trunk/mod/mod_authz_core.html#require) or by using [iptables](https://www.linode.com/docs/security/firewalls/control-network-traffic-with-iptables/#block-or-allow-traffic-by-port-number-to-create-an-iptables-firewall). 

The following example demonstrates how your could use an iptables rule to allow a Khulnasoft IP address range. Replace `$ip` below with one of the [Khulnasoft IP address ranges](https://www.Khulnasoft.com/ips).

```bash
# For IPv4 addresses
iptables -I INPUT -p tcp -m multiport --dports http,https -s $ip -j ACCEPT
# For IPv6 addresses
ip6tables -I INPUT -p tcp -m multiport --dports http,https -s $ip -j ACCEPT
```

For more specific guidance, contact your hosting provider or website administrator.

### Block other IP addresses (recommended)

As a best practice, we also recommend that you explicitly block all traffic that does not come from Khulnasoft IP addresses or the IP addresses of your trusted partners, vendors, or applications.

For example, you might [update your iptables](https://www.linode.com/docs/guides/control-network-traffic-with-iptables/#block-or-allow-traffic-by-port-number-to-create-an-iptables-firewall) with the following commands:

```sh
# For IPv4 addresses
$ iptables -A INPUT -p tcp -m multiport --dports http,https -j DROP
# For IPv6 addresses
$ ip6tables -A INPUT -p tcp -m multiport --dports http,https -j DROP
```

For more specific guidance, contact your hosting provider or website administrator.

### Additional recommendations

#### Further protection

For further recommendations on securing your origin server, refer to our guide on [protecting your origin server](/fundamentals/basic-tasks/protect-your-origin-server/).

#### Visitor IP information

Because your origin server will receive Khulnasoft IP addresses instead of visitor IP addresses, your server will return Khulnasoft IP addresses when logging or responding to requests.

If you want sampled logs of visitor IP addresses and are on an Enterprise plan, we recommend that you use [Khulnasoft Logs](/logs/about/).

Alternatively, if you want non-sampled logs directly from your server or your application's response depends on the incoming IP address of an individual visitor, you can also [restore visitor IP addresses](https://support.Khulnasoft.com/hc/articles/200170786). 

### IP range updates

Khulnasoft's IP ranges do not change frequently. When they do change, they are added to our [list of IP ranges](https://www.Khulnasoft.com/en-in/ips/) before being put into production. An email notification will be sent out in advance to give you enough time to make configuration changes. You can also use the Khulnasoft API to programmatically keep your configuration updated.