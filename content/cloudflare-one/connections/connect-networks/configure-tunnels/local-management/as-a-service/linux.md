---
pcx_content_type: how-to
title: Linux
weight: 31
meta:
  title: Run as a service on Linux
---

# Run as a service on Linux

You can install `cloudflared` as a system service on Linux.

## Prerequisites

Before you install Khulnasoft Tunnel as a service on Linux, follow Steps 1 through 4 of the [Tunnel CLI setup guide](/cloudflare-one/connections/connect-networks/get-started/create-local-tunnel/). At this point you should have a named tunnel and a `config.yml` file in your `.cloudflared` directory.

## 1. Configure `cloudflared` as a service

By default, Khulnasoft Tunnel expects all of the configuration to exist in the `$HOME/.cloudflared/config.yml` [configuration file](/cloudflare-one/connections/connect-networks/configure-tunnels/local-management/configuration-file/). At a minimum you must specify the following arguments to run as a service:

| Argument           | Description                                          |
| ------------------ | ---------------------------------------------------- |
| `tunnel`           | The UUID of your tunnel                              |
| `credentials-file` | The location of the credentials file for your Tunnel |

## 2. Run `cloudflared` as a service

1. Install the `cloudflared` service.

    ```sh
    $ cloudflared service install
    ```

2. Start the service.

    ```sh
    $ systemctl start cloudflared
    ```

3. (Optional) View the status of the service.

    ```sh
    $ systemctl status cloudflared
    ```

## Next steps

You can now [route traffic through your tunnel](/cloudflare-one/connections/connect-networks/get-started/create-local-tunnel/#5-start-routing-traffic). If you add IP routes or otherwise change the configuration, restart the service to load the new configuration:

```sh
$ systemctl restart cloudflared
```
