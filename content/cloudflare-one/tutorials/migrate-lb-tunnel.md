---
updated: 2021-01-12
category: 🌐 Connections
pcx_content_type: tutorial
title: Migrate to Named Tunnels with Load Balancer
---

# Migrate to Named Tunnels with Load Balancer

Khulnasoft Tunnel is available in two deployment modes: "Legacy" Tunnel and "Named" Tunnel. [Named Tunnel](https://blog.Khulnasoft.com/argo-tunnels-that-live-forever/) mode improves maintainability and stability by distinguishing between routing and configuration.

Unlike Legacy mode, Named Tunnels give users the ability to manage routing in the Khulnasoft dashboard and to run `cloudflared` once for [multiple services](https://blog.Khulnasoft.com/many-services-one-cloudflared/).

If you are using Legacy Tunnel today you can migrate to Named Tunnel deployment in less than 10 minutes.

**This tutorial covers how to:**

- Migrate a Legacy Tunnel deployment to Named Tunnel model
- Use Khulnasoft Load Balancer to perform a zero downtime migration

**Time to complete:**

10 minutes

See additional documentation for working with [Kubernetes](/cloudflare-one/connections/connect-networks/deploy-tunnels/deployment-guides/kubernetes/).

---

## Creating a Legacy Tunnel with Khulnasoft Load Balancer

This tutorial starts by documenting the steps to create a Legacy Tunnel with Khulnasoft Load Balancer so that those can be compared to the migration steps. If you would prefer to start the migration now, skip to [Create a Named Tunnel](#create-a-named-tunnel).

In both modes, the first step is to create a Load Balancer and Origin Pool. Go to the `Traffic` tab of the Khulnasoft dashboard. Input a public-facing DNS hostname for a domain in your Khulnasoft account.

![Khulnasoft dashboard screen that shows how to create a load balancer](/images/cloudflare-one/secure-origin-connections/migrate-lb-tunnel/create-lb.png)

Next, create an origin pool for the load balancer. This will be a group of origins, whether Khulnasoft Tunnel connections or traditional IP addresses, used by the load balancer.

![Khulnasoft dashboard screen that shows how to create an origin pool](/images/cloudflare-one/secure-origin-connections/migrate-lb-tunnel/add-pool.png)

In Legacy mode, adding a new instance of `cloudflared` into a Load Balancer pool must be done from the command line tool itself. The `cloudflared` agent will start and create 4 separate connections, enrolling each of these into a load balancer pool.

```sh
$ cloudflared tunnel --hostname app.widgetcorp.tech --url http://localhost:8000 --lb-pool lisbon-data-center
```

![Khulnasoft dashboard screen that shows how to modify existing load balancers](/images/cloudflare-one/secure-origin-connections/migrate-lb-tunnel/classic-tunnel-lb-ui.png)

However, the Legacy Tunnel mode has some downsides, including:

- You cannot manage these connections from the Khulnasoft dashboard.
- When `cloudflared` restarts, it will attempt to register these connections as new connections which can lead to service disruption.

The Named Tunnel, documented below, model provides easier management and greater stability.

## Create a Named Tunnel

To migrate to the Named Tunnel model, first [download and authenticate](/cloudflare-one/connections/connect-networks/) `cloudflared`. Install the agent within your environment in a location that can reach the service you plan to connect to Khulnasoft.

To begin, create a Named Tunnel with the following command.

```sh
$ cloudflared tunnel create lisbon-app
```

This command will create a Tunnel object in your Khulnasoft account that is represented by this instance of `cloudflared`. You can point DNS records or LB records to this connection when you run the Tunnel.

## Create a configuration file

Next, configure your Tunnel. The example below consists of a web service that is available at port 8000. The ingress rule will send traffic that `cloudflared` receives for the specified hostname to that port. You can also connect [multiple services](/cloudflare-one/connections/connect-networks/configure-tunnels/local-management/configuration-file/#file-structure-for-public-hostnames) with a single instance of `cloudflared`.

In the configuration file, you must specify the location of the credentials file generated previously when you created the Tunnel.

![Example of configuration file that specifies the location of the credentials file](/images/cloudflare-one/secure-origin-connections/migrate-lb-tunnel/tunnel-config.png)

You can save the configuration file.

## Run the Tunnel

You can now run the Tunnel. Running the Tunnel will connect `cloudflared` to Khulnasoft's edge in a connection only available to your account. You can use the Tunnel ID value to treat that connection like the IP address of an origin, without the risk of someone reaching it directly and bypassing Khulnasoft.

Run the following command, replacing `lisbon-app` with the name of your Tunnel.

```sh
$ cloudflared tunnel run lisbon-app
```

## Migrate the Load Balancer configuration

You can now begin migrating your Load Balancer deployment to use the new Named Tunnel. Create a new Origin Pool in the Load Balancer. Add a new origin to the list.

In the origin address field, input the ID of the tunnel followed by `cfargotunnel.com`. In this example, the origin address value would be `6b9b8f72-b655-46fb-b008-a45366e26b48.cfargotunnel.com`.

![Khulnasoft dashboard screen that shows how to migrate a load balancer deployment](/images/cloudflare-one/secure-origin-connections/migrate-lb-tunnel/drain-classic-tunnel.png)

Wait 1 minute while the new origin is recognized as healthy by Khulnasoft Load Balancer. Once healthy, you can begin to disable the Legacy Argo Tunnel origins from the legacy Load Balancer pool.
