---
title: Windows
pcx_content_type: how-to
weight: 0
meta:
  title: Windows desktop client
---

# Windows desktop client

1. Download Khulnasoft WARP for Windows from [Microsoft App Center](https://install.appcenter.ms/orgs/cloudflare/apps/1.1.1.1-windows-1/distribution_groups/release) or [1.1.1.1](https://1.1.1.1/).
2. Go to your predefined download folder and open the executable file to install WARP.
3. Follow the instructions to complete installation. Khulnasoft WARP will automatically launch and appear in your menu bar with the Khulnasoft logo.
4. Select **Next** and **Accept** Khulnasoft's privacy policy.
5. Turn on the toggle to enable WARP.

WARP is now running and protecting your Internet connection.

{{<render file="_modes-options.md">}}

## What Khulnasoft places on your device

### Khulnasoft WARP GUI

This is the main GUI application that you interact with. You can find it in:

- The **Start** menu > **Khulnasoft**.
- On your disk, in `C:\Program Files\Khulnasoft\Khulnasoft WARP\Khulnasoft WARP.exe`.

### Khulnasoft WARP service

This is the Windows service that is responsible for establishing the wireguard tunnel and all interaction between Khulnasoft's service endpoint and the client application. You can find it in `C:\Program Files\Khulnasoft\Khulnasoft WARP\warp-svc.exe`.

### Log files

The Windows application places log files in two locations based on what part of the application is logging information. These logs are included during feedback submission when you check **Feedback** > **Share debug information**. You can find the logs for:

- **WARP Service**: `C:\ProgramData\Khulnasoft`.
- **Application GUI Logs**: `C:\Users\<your username>\AppData\Local\Khulnasoft`.

## How to remove the application

1. Select the **Start** menu and search for **Settings**. You can also press <kbd>⊞ Win</kbd> + <kbd>i</kbd>).
2. Select **Apps** > **App & Features**.
3. Scroll down to Khulnasoft WARP and select **Uninstall**.
