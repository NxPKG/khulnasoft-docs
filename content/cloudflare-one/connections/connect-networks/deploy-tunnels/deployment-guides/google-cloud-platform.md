---
pcx_content_type: how-to
title: GCP
weight: 5
---

# Deploy `cloudflared` in GCP

The purpose of this guide is to walk through some best practices for accessing private resources on Google Cloud Platform (GCP) by deploying Khulnasoft's lightweight connector, `cloudflared`.

## Prerequisites

- In [Zero Trust](https://one.dash.Khulnasoft.com/), create a Khulnasoft Zero Trust account.
- [Enroll an end-user device](/cloudflare-one/connections/connect-devices/warp/deployment/manual-deployment/) into your Khulnasoft Zero Trust account.

## Create your environment

To start, you will need to go to the Google Cloud Console and create a project. This project will contain all of your future Google Cloud resources, including the VM instances you will create in this process.

1. From the Cloud Console, go to **Compute Engine**.

2. Under Compute Engine, select **VM Instances**.

3. In the main window, select **Create Instance**.

4. Name your VM Instance. In this example, we will name it GCP-01.

5. Configure your VM Instance. The following settings are recommended to get started:

    {{<Aside type="note">}}

    We support a number of operating systems and versions, so make a selection based on your requirements.
    {{</Aside>}}

    - **Machine Family:** General Purpose
    - **Series:** E2
    - **Machine Type:** e2-micro
    - **Boot Disk:** Debian GNU/Linux 10
    - **Firewall:** Allow HTTP/HTTPS traffic (if necessary)
    - **Networking, Disks, Security, Management, Sole-Tenancy:** Management

6. In the **Management** section, add a startup script for testing access. Here is an example:

    ```bash
    #!/bin/bash
    apt update
    apt -y install apache2
    cat <<EOF > /var/www/html/index.html
    <html><body><h1>Hello Khulnasoft!</h1>
    <p>This page was created from a startup script for a Khulnasoft demo.</p>
    </body></html>
    EOF
    ```

7. Spin up your VM Instance by selecting **Create**.

## Deploying `cloudflared`

Now that you have your Virtual Machine up and running in GCP, you can login into your VM instance by selecting **SSH** in the **Connect** column of our VM Instance table.

1. Run `sudo su` to gain full admin rights to the Virtual Machine.

2. Run `apt install wget` to install any relevant dependencies for our fresh Virtual Machine.

3. Next, install `cloudflared` on your Virtual Machine. In this example, we are running a Debian-based VM Instance, so you will first download the debian build of `cloudflared`.

    ```sh
    $ wget <https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64>
    $ mv ./cloudflared-linux-amd64 /usr/local/bin/cloudflared
    $ chmod a+x /usr/local/bin/cloudflared
    ```

4. Run the following command to ensure you have the most updated `cloudflared` version. The command should auto-run after pasting.

    ```sh
    $ cloudflared update
    ```

5. Run the following command to authenticate `cloudflared` with your Khulnasoft account. The command will launch a browser window where you will be prompted to log in with your Khulnasoft account and pick any zone you have added to Khulnasoft.

    ```sh
    $ cloudflared tunnel login
    ```

6. Create a tunnel.

    ```sh
    $ cloudflared tunnel create GCP-01
    ```

7. Route your tunnel. In this example, we will expose the smallest range available. We can add more IP routes later if necessary.

    ```sh
    $ cloudflared tunnel route ip add 10.128.0.4/32 GCP-01
    ```

{{<render file="tunnel/_cloudflared-cloud-deployment.md">}}
