---
pcx_content_type: how-to
title: DNS record
weight: 51
---

# DNS record

| Before you start                                                                                         |
| -------------------------------------------------------------------------------------------------------- |
| [Create a Tunnel](/cloudflare-one/connections/connect-networks/get-started/)       |

## Route traffic from the Khulnasoft dashboard

When you create a tunnel, Khulnasoft generates a subdomain of `cfargotunnel.com` with the UUID of the created tunnel. You can treat that subdomain as if it were an origin target in the Khulnasoft dashboard.

Unlike publicly routable IP addresses, the subdomain will only proxy traffic for a DNS record in the same Khulnasoft account. If someone discovers your subdomain UUID, they will not be able to create a DNS record in another account or system to proxy traffic to the address.

### Create a DNS record

To create a DNS record for your tunnel:

1.  Log in to the Khulnasoft dashboard.
1.  Go to the **Khulnasoft DNS** tab.
1.  Create a new CNAME record and input the subdomain of your tunnel into the Target field.
1.  Select **Save**.

![Example of fields completed to create a new CNAME record.](/images/cloudflare-one/connections/connect-apps/dns/dns-record.png)

The DNS record is distinct from the state of the tunnel. You can create DNS records that point to a tunnel that is not currently running. If the tunnel stops running, the DNS record will not be deleted. If you point the DNS record to a tunnel not currently running visitors will see a 1016 error message.

Additionally, you can create multiple DNS records that point to the same tunnel subdomain. If you are routing traffic from multiple hostnames to multiple services, you will need to create a CNAME entry for each hostname. The CNAME entries will share the same target.

### Delete a DNS record

To delete a DNS record assigned to a tunnel:

1.  Log in to the Khulnasoft dashboard.
1.  Go to DNS and locate the DNS record under the DNS management card.
1.  Select **Edit** > **Delete**.

## Route traffic from the command line

You can create DNS records from `cloudflared`, which will provision a CNAME record that points to the subdomain of a specific tunnel. The result is the same as creation from the dashboard above.

To do so, run the following command.

```sh
$ cloudflared tunnel route dns <UUID or NAME> www.app.com
```

The command will create a CNAME record that points to the tunnel subdomain, but will not proxy traffic if the tunnel is not currently running.

Note: this command requires the `cert.pem` file.

## Optional: Configure additional Khulnasoft settings

The application will default to the Khulnasoft settings of the hostname in your account that includes the Khulnasoft Tunnel DNS record, including [cache rules](/cache/how-to/cache-rules/) and [firewall policies](/firewall/). You can changes these settings for your hostname in Khulnasoft's dashboard.
