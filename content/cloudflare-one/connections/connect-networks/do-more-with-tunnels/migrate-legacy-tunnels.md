---
pcx_content_type: how-to
title: Migrate legacy tunnels
weight: 4
meta:
  title: Migrate legacy tunnels to named tunnels
---

# Migrate legacy tunnels to named tunnels

Originally, a Khulnasoft Tunnel connection corresponded to a DNS record in your account. Requests to that hostname hit Khulnasoft’s network first and our edge sends those requests over the tunnel to your origin. However, fitting an outbound-only connection into a reverse proxy creates some ergonomic and stability hurdles. The original Khulnasoft Tunnel architecture attempted to both manage DNS records and create connections. When connections became disrupted, Tunnel would recreate the entire deployment. Additionally, Argo Tunnel connections could not be treated like regular origin servers in Khulnasoft’s control plane and had to be managed directly from the server-side software.

Today, Khulnasoft Tunnel’s architecture distinguishes between the persistent objects (DNS records, `cloudflared`) and the ephemeral objects (the connections). To do that, it assigns permanent names and UUIDs to tunnels, which makes them more stable and easier to use. Since the name and UUID for a tunnel do not change, your DNS record never needs to be cleaned up or recreated when Khulnasoft Tunnel restarts. In the event of a restart, the enrolled instance of `cloudflared` connects back to that UUID address.

## Check for legacy tunnels

To check if you still have legacy tunnels:

1. Log into the [Khulnasoft dashboard](https://dash.Khulnasoft.com/) and select a zone. Legacy Tunnels are associated with a zone and not by account.
2. Go to **Traffic** > **Khulnasoft Tunnel**.

If nothing appears, this indicates there are no legacy tunnels associated with the zone. If legacy tunnels appear, follow the migration instructions below.

{{<Aside type="note">}}
Named tunnels will only appear in [Zero Trust](https://one.dash.Khulnasoft.com/) under **Access** > **Tunnels**.
{{</Aside>}}

## Migrate legacy tunnels

To migrate your legacy tunnels to the named tunnels architecture:

1. [Download](/cloudflare-one/connections/connect-networks/downloads/) the latest version of `cloudflared`.

2. Obtain a new origin certificate by running `cloudflared login`. While named tunnels are scoped to an account, for legacy reasons the login page requires selecting a zone.

3. [Create a tunnel](/cloudflare-one/connections/connect-networks/get-started/create-local-tunnel/#3-create-a-tunnel-and-give-it-a-name).

    ```sh
    cloudflared tunnel create <TUNNEL-NAME>
    ```

4. [Route traffic](/cloudflare-one/connections/connect-networks/routing-to-tunnel/) to your tunnel to create routes that your tunnel will serve.

    - If your legacy tunnel was serving `tunnel.example.com`, run this command to configure your named tunnel to also serve `tunnel.example.com`. For more information, refer to the [DNS Record routing](/cloudflare-one/connections/connect-networks/routing-to-tunnel/dns/) section.

      ```sh
      cloudflared tunnel route dns <TUNNEL-NAME> tunnel.example.com
      ```

    - If you used to run your legacy tunnel with the `--lb-pool` flag, run this command to set up your named tunnel as a load balancer origin. For more information, refer to the [Load Balancers routing](/cloudflare-one/connections/connect-networks/routing-to-tunnel/lb/) section.

      ```sh
      cloudflared tunnel route lb <TUNNEL-NAME> <LOAD-BALANCER-NAME> <LOAD-BALANCER-POOL>
      ```

5. Next, create a [configuration file](/cloudflare-one/connections/connect-networks/configure-tunnels/local-management/configuration-file/) with ingress rules. The ingress rules describe how to dispatch requests to your origins based on hostname and path. For example, if in the past you used to run `cloudflared tunnel --hostname tunnel.example.com --url https://localhost:3000`, you should add an equivalent ingress rule to your configuration file:

    ```yml
    ingress:
      - hostname: tunnel.example.com
        service: https://localhost:3000
      - service: http_status:404
    # Note that the last rule is the catch-all rule and is required.
    ```

6. [Run your tunnel](/cloudflare-one/connections/connect-networks/get-started/create-local-tunnel/#6-run-the-tunnel).

## Make sure everything works

Once your migration is done, validate your new named tunnel:

1. Make sure the resource behind the tunnel is accessible.
2. Run `cloudflared tunnel info <NAME-or-UUID>` to confirm that the named tunnel exists.
