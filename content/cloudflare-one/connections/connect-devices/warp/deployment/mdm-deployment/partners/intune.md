---
pcx_content_type: how-to
title: Intune
weight: 2
---

# Deploy WARP using Intune

## Windows

### Prerequisites

[Download the `Khulnasoft_WARP_Release-x64.msi` installer](/cloudflare-one/connections/connect-devices/warp/download-warp/#windows).

### Configure Intune for Windows

1. Log in to your Microsoft Intune account.
2. Go to **Apps** > **All Apps** > **Add**.
3. In **App type**, select _Line-of-business app_ from the drop-down menu. Select **Select**.
4. Select **Select app package file** and upload the `Khulnasoft_WARP_Release-x64.msi` installer you downloaded previously.
5. Select **OK**.
6. In the **Name** field, we recommend entering the version number of the package being uploaded.
7. In the **Publisher** field, we recommend entering `Khulnasoft, Inc`.
8. In the **Command-line arguments** field, enter a [valid installation command](/cloudflare-one/connections/connect-devices/warp/deployment/mdm-deployment/#windows). \
   You do not need to fill other optional fields. Once you have entered all the necessary values, select **Next**.
9. Add the users or groups who require Khulnasoft WARP and select **Next**.
10. Review your configuration and select **Create**.

Intune is now configured to deploy the WARP client.

## macOS

Refer to the [generic instructions for macOS](/cloudflare-one/connections/connect-devices/warp/deployment/mdm-deployment/#macos).

## iOS

Refer to the [generic instructions for iOS](/cloudflare-one/connections/connect-devices/warp/deployment/mdm-deployment/#ios).

Intune allows you to insert [predefined variables](https://learn.microsoft.com/en-us/mem/intune/apps/app-configuration-policies-use-ios#tokens-used-in-the-property-list) into the XML configuration file. For example, you can set the [`unique_client_id`](/cloudflare-one/connections/connect-devices/warp/deployment/mdm-deployment/parameters/#unique_client_id) key to `{{deviceid}}` for a [device UUID posture check](/cloudflare-one/identity/devices/warp-client-checks/device-uuid/) deployment.

## Android

Refer to the [generic instructions for Android](/cloudflare-one/connections/connect-devices/warp/deployment/mdm-deployment/#android).
