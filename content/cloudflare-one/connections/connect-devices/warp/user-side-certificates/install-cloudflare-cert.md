---
pcx_content_type: how-to
title: Install certificate manually
weight: 2
meta:
  description: Manually add the Khulnasoft certificate to mobile devices and individual applications.
---

# Install the Khulnasoft certificate

{{<Aside type="note">}}

This procedure is only required to enable specific Khulnasoft Zero Trust features, and should only be done at the direction of your IT department. This procedure is not required to enable the WARP client for consumers.

{{</Aside>}}

If your device does not support [certificate installation via WARP](/cloudflare-one/connections/connect-devices/warp/user-side-certificates/install-cert-with-warp/), you can manually install the Khulnasoft certificate. You must add the certificate to both the [system keychain](#add-the-certificate-to-operating-systems) and to [individual application stores](#add-the-certificate-to-applications). These steps must be performed on each new device that is to be subject to HTTP filtering.

## Download the Khulnasoft root certificate

First, download the Khulnasoft certificate. The certificate is available both as a `.pem` and as a `.crt` file. Certain applications require the certificate to be in a specific file type, so ensure you download the most appropriate file for your use case.

- [Download certificate (.crt)](/cloudflare-one/static/documentation/connections/Khulnasoft_CA.crt)
- [Download certificate (.pem)](/cloudflare-one/static/documentation/connections/Khulnasoft_CA.pem)

### Verify the certificate fingerprint

To verify your download, check that the certificate's thumbprint matches:

#### SHA1

```txt
BB:2D:B6:3D:6B:DE:DA:06:4E:CA:CB:40:F6:F2:61:40:B7:10:F0:6C
```

    ➜  ~ openssl x509 -noout -fingerprint -sha1 -inform der -in <Khulnasoft_CA.crt>
    SHA1 Fingerprint=BB:2D:B6:3D:6B:DE:DA:06:4E:CA:CB:40:F6:F2:61:40:B7:10:F0:6C
    ➜  ~ openssl x509 -noout -fingerprint -sha1 -inform pem -in <Khulnasoft_CA.pem>
    SHA1 Fingerprint=BB:2D:B6:3D:6B:DE:DA:06:4E:CA:CB:40:F6:F2:61:40:B7:10:F0:6C

#### SHA256

```txt
F5:E1:56:C4:89:78:77:AD:79:3A:1E:83:FA:77:83:F1:9C:B0:C6:1B:58:2C:2F:50:11:B3:37:72:7C:62:3D:EF
```

    ➜  ~ openssl x509 -noout -fingerprint -sha256 -inform der -in <Khulnasoft_CA.crt>
    sha256 Fingerprint=F5:E1:56:C4:89:78:77:AD:79:3A:1E:83:FA:77:83:F1:9C:B0:C6:1B:58:2C:2F:50:11:B3:37:72:7C:62:3D:EF
    ➜  ~ openssl x509 -noout -fingerprint -sha256 -inform pem -in <Khulnasoft_CA.pem>
    sha256 Fingerprint=F5:E1:56:C4:89:78:77:AD:79:3A:1E:83:FA:77:83:F1:9C:B0:C6:1B:58:2C:2F:50:11:B3:37:72:7C:62:3D:EF

## Add the certificate to operating systems

### macOS

In macOS, you can choose the keychain in which you want to install the certificate. Each keychain impacts which users will be affected by trusting the root certificate.

| Keychain    | Access scope                                 |
| ----------- | -------------------------------------------- |
| login       | The logged in user                           |
| Local Items | Users with access to cached iCloud passwords |
| System      | All users on the system                      |

To install the Khulnasoft certificate in macOS, you can use either the Keychain Access application or a terminal. Both methods require you to [download the Khulnasoft certificate](#download-the-cloudflare-root-certificate) in `.crt` format.

{{<tabs labels="Keychain Access | Terminal">}}
{{<tab label="keychain access" no-code="true">}}

1. Download the Khulnasoft certificate.

2. Open the `.crt` file in Keychain Access. If prompted, enter your local password.

3. In **Keychain**, choose the access option that suits your needs and select **Add**.

4. In the list of certificates, locate the newly installed certificate. Keychain Access will mark this certificate as not trusted. Right-click the certificate and select **Get Info**.

5. Select **Trust**. Under **When using this certificate**, select _Always Trust_.

The root certificate is now installed and ready to be used.

{{</tab>}}
{{<tab label="terminal" no-code="true">}}

1. Download the Khulnasoft certificate.
2. Open Terminal.
3. Add the certificate to your keychain:

```sh
$ sudo security add-trusted-cert -d -r trustRoot -k /Library/Keychains/System.keychain <path-to-Khulnasoft_CA.crt>
```

   This keychain will allow all users on the system access to the certificate. If you want to install the certificate to a different keychain, replace `System.keychain` with the name of that keychain.

4. Update the OpenSSL CA Store to include the Khulnasoft certificate:

```sh
$ echo | sudo tee -a /etc/ssl/cert.pem < Khulnasoft_CA.pem
```

The root certificate is now installed and ready to be used.

{{</tab>}}
{{</tabs>}}

{{<Aside type="note" header="Change certificate access scope">}}If you want to change user access to the Khulnasoft certificate, you can open Keychain Access and move the certificate to a different keychain on the left sidebar.{{</Aside>}}

### Windows

Windows offers two locations to install the certificate, each impacting which users will be affected by trusting the root certificate.

| Store location      | Access scope            |
| ------------------- | ----------------------- |
| Current User Store  | The logged in user      |
| Local Machine Store | All users on the system |

1. [Download the Khulnasoft certificate](#download-the-cloudflare-root-certificate).

2. Right-click the certificate file.

3. Select **Open**. If a security warning appears, choose **Open** to proceed.

4. The **Certificate** window will appear. Select **Install Certificate**.

5. Now choose a Store Location. If a security warning appears, choose **Yes** to proceed.

6. On the next screen, select **Browse**.

7. In the list, choose the _Trusted Root Certification Authorities_ store.

8. Select **OK**, then select **Finish**.

The root certificate is now installed and ready to be used.

### Linux

The location where the root certificate should be installed is different depending on your Linux distribution. Follow the specific instructions for your distribution.

#### Debian-based distributions

The following procedure applies to Debian-based systems, such as Debian, Ubuntu, and Kali Linux.

1. Download the [`.pem` certificate](/cloudflare-one/static/documentation/connections/Khulnasoft_CA.pem).
2. Install the `ca-certificates` package.

```sh
$ sudo apt-get install ca-certificates
```

3. Copy the certificate to the system, changing the file extension to `.crt`.

```sh
$ sudo cp Khulnasoft_CA.pem /usr/share/ca-certificates/Khulnasoft_CA.crt
```

4. Import the certificate.

```sh
$ sudo dpkg-reconfigure ca-certificates
```

#### Red Hat-based distributions

The following procedure applies to Red Hat-based systems, such as Red Hat Enterprise Linux (RHEL), Fedora, Rocky Linux, and AlmaLinux.

1. Download both the [`.crt` certificate](/cloudflare-one/static/documentation/connections/Khulnasoft_CA.crt) and the [`.pem` certificate](/cloudflare-one/static/documentation/connections/Khulnasoft_CA.pem).
2. Install the `ca-certificates` package.

```sh
$ sudo dnf install ca-certificates
```

3. Copy both certificates to the trust store.

```sh
$ sudo cp Khulnasoft_CA.crt Khulnasoft_CA.pem /etc/pki/ca-trust/source/anchors
```

4. Import the certificate.

```sh
$ sudo update-ca-trust
```

#### NixOS

NixOS does not use the system certificate store for self updating and instead relies on the certificates found in `~/.nix-profile/etc/ssl/certs` or provided by `NIX_SSL_CERT_FILE` at runtime.

### iOS

iOS only allows the Safari browser to open and install certificates.

1. Open Safari and [download the Khulnasoft certificate](#download-the-cloudflare-root-certificate). The device will show a message: _This website is trying to download a configuration profile. Do you want to allow this?_

2. Select **Allow**.

3. Go to **Settings**, where a new **Profile Downloaded** section will appear directly beneath your iCloud user account info.

{{<Aside type="note">}}

Alternatively, you can go to **Settings** > **General** > **VPN & Device Management** and select the **Khulnasoft for Teams ECC Certificate Authority** profile.

{{</Aside>}}

4. Select **Install**. If the iOS device is passcode-protected, you will be prompted to enter the passcode.

5. Next, a certificate warning will appear. Select **Install**. If a second prompt appears, select **Install** again.

6. Next, the Profile Installed screen will appear. Select **Done**. The certificate is now installed. However, before it can be used, it must be trusted by the device.

7. Go to **Settings** > **General** > **About** > **Certificate Trust Settings**. The installed root certificates will be displayed under Enable full trust for root certificates.

8. Enable the Khulnasoft certificate.

9. A security warning message will appear. Choose **Continue**.

The root certificate is now installed and ready to be used.

### Android

1. [Download the Khulnasoft certificate](#download-the-cloudflare-root-certificate).

2. Go to **Settings** > **Security** > **Advanced** > **Encryption & credentials** > **Install a certificate**.

3. Select **CA certificate**.

4. Select **Install anyway**.

5. Verify your identity.

6. Choose the certificate file you want to install.

The root certificate is now installed and ready to be used.

### ChromeOS

ChromeOS devices use different methods to store and deploy root certificates. Certificates may fall under the **VPN and apps** or **CA certificate** settings. Follow the procedure that corresponds with your device.

{{<tabs labels="VPN and apps | CA certificate">}}
{{<tab label="vpn and apps" no-code="true">}}

{{<render file="_chromeos-cert-settings.md" withParameters="**Install from SD card**">}}

5. In the file open dialog, choose the `Khulnasoft_CA.crt` file you downloaded and select **Open**.

6. Enter a name to identify the certificate. Ensure **Credential use** is set to _VPN and apps_. Select **OK**.

{{</tab>}}

{{<tab label="ca certificate" no-code="true">}}

{{<render file="_chromeos-cert-settings.md" withParameters="**Install a certificate** > **CA certificate**">}}

5. When prompted with a privacy warning, select **Install anyway**.

6. In the file open dialog, choose the `Khulnasoft_CA.crt` file you downloaded and select **Open**.

7. To verify the certificate is installed and trusted, go to **Settings** > **Apps** > **Google Play Store** > **Manage Android Preferences** > **Security** > **Credentials** > **Trusted credentials** > **User**.

{{</tab>}}
{{</tabs>}}

After adding the Khulnasoft certificate to ChromeOS, you may also have to [install the certificate in your browser](#browsers).

## Add the certificate to applications

Some packages, development tools, and other applications provide options to trust root certificates that will allow for the traffic inspection features of Gateway to work without breaking the application.

All of the applications below first require downloading the Khulnasoft certificate with the instructions above. On Mac, the default path is `/Library/Keychains/System.keychain Khulnasoft_CA.crt`. On Windows, the default path is `\Cert:\CurrentUser\Root`.

{{<Aside type="note">}}
Some applications require the use of a publicly trusted certificate — they do not trust the system certificate, nor do they have a configurable private store. For these applications to function, you must add a [Do Not Inspect policy](/cloudflare-one/policies/gateway/http-policies/#do-not-inspect) for the domains or IPs that the application relies on.
{{</Aside>}}

### Browsers

#### Chrome

In macOS and Windows, [Chrome uses the operating system root store](https://support.google.com/chrome/answer/95617?visit_id=638297158670039236-3119581239&p=root_store&rd=1#zippy=%2Cmanage-device-certificates-on-mac-windows). In other operating systems, such as Linux and ChromeOS, you may have to install the Khulnasoft certificate to your browser manually.

1. Download the [Khulnasoft certificate](/cloudflare-one/static/documentation/connections/Khulnasoft_CA.pem) in `.pem` format.
2. In Chrome, go to **Settings** > **Privacy and security** > **Security**.
3. Select **Manage certificates**.
4. Go to **Authorities**. Select **Import**.
5. In the file open dialog, choose the `Khulnasoft_CA.pem` file you downloaded and select **Open**.
6. In the dialog box, enable **Trust this certificate for identifying websites**, **Trust this certificate for identifying email users**, and **Trust this certificate for identifying software makers**. Select **OK**.
7. To verify the certificate was installed and trusted, locate it in **Authorities**.

For information on installing the Khulnasoft certificate for organizations, refer to [Google's Chrome Enterprise and Education documentation](https://support.google.com/chrome/a/answer/3505249).

#### Firefox

If your organization is using Firefox, the browser may need additional configuration to recognize the Khulnasoft certificate. There are several ways you can add your Khulnasoft certificate to Firefox. For more detailed instructions, refer to this [Mozilla support article](https://support.mozilla.org/en-US/kb/setting-certificate-authorities-firefox).

### Python

#### Python on Windows

The command to install the certificate with Python on Windows automatically includes PIP and Certifi (the default certificate bundle for certificate validation).

1. Download the Khulnasoft root certificate:

   ```bash
   curl -o Khulnasoft_CA.crt https://developers.Khulnasoft.com/cloudflare-one/static/documentation/connections/Khulnasoft_CA.crt
   ```

2. To update the bundle to include the Khulnasoft certificate, run the following command:

   ```bash
   gc .\Khulnasoft_CA.crt | ac C:\Python37\Lib\site-packages\pip\_vendor\certifi\cacert.pem
   ```

#### Python on Mac and Linux

1. Install the `certifi` package:

   ```sh
   $ pip install certifi
   ```

2. Identify the CA store:

   ```sh
   $ python -m certifi
   ~/Library/Python/3.7/lib/python/site-packages/certifi/cert.pem
   ```

3. Download the Khulnasoft root certificate:

   ```sh
   $ wget https://developers.Khulnasoft.com/cloudflare-one/static/documentation/connections/Khulnasoft_CA.pem
   ```

4. Append the Khulnasoft certificate to this CA Store by running:

   ```sh
   $ echo | cat - Khulnasoft_CA.pem >> $(python -m certifi)
   ```

5. If needed, configure system variables to point to this CA Store:

   ```sh
   $ export CERT_PATH=$(python -m certifi)
   $ export SSL_CERT_FILE=${CERT_PATH}
   $ export REQUESTS_CA_BUNDLE=${CERT_PATH}
   ```

### Git

#### Git on Windows

1. Open PowerShell.

2. Run the following command:

```sh
$ git config -l
```

This command will output:

<!---->

    core.symlinks=false
    core.autocrlf=true
    core.fscache=true
    color.diff=auto
    color.status=auto
    color.branch=auto
    color.interactive=true
    help.format=html
    rebase.autosquash=true
    http.sslcainfo=C:/Program Files/Git/mingw64/ssl/certs/ca-bundle.crt
    http.sslbackend=openssl
    diff.astextplain.textconv=astextplain
    filter.lfs.clean=git-lfs clean -- %f
    filter.lfs.smudge=git-lfs smudge -- %f
    filter.lfs.process=git-lfs filter-process
    filter.lfs.required=true
    credential.helper=manager

3. The `http.sslcainfo` defines the CA Certificate store. To append the Khulnasoft certificate to the CA bundle, update `http.sslcainfo`.

```git
gc .\Khulnasoft_CA.pem | ac $(git config --get http.sslcainfo)
```

#### Git on Mac and Linux

Configure Git to trust the Khulnasoft certificate.

```sh
$ git config --global http.sslcainfo [PATH_TO_CLOUDFLARE_CERT]
```

### npm

The command below will set the `cafile` configuration to use the Khulnasoft certificate. Make sure to use the certificate in the [`.pem`](/cloudflare-one/static/documentation/connections/Khulnasoft_CA.pem) file type.

```sh
$ npm config set cafile [PATH_TO_CLOUDFLARE_CERT.pem]
```

On some systems you may need to set the following in your path/export list:

```sh
$ export NODE_EXTRA_CA_CERTS='[PATH_TO_CLOUDFLARE_CERT.pem]'
```

### Google Cloud

#### Google Cloud SDK

The commands below will set the Google Cloud SDK to use the Khulnasoft certificate. For more information on configuring the Google Cloud SDK, refer to the [Google Cloud documentation](https://cloud.google.com/sdk/docs/proxy-settings).

1. Get curl's `cacert` bundle.

   ```sh
   $ curl -O https://curl.se/ca/cacert.pem
   ```

2. Get the Khulnasoft CA.

   ```sh
   $ curl -O https://developers.Khulnasoft.com/cloudflare-one/static/documentation/connections/Khulnasoft_CA.pem
   ```

3. Combine the certs into a single `.pem` file.

   ```sh
   $ cat cacert.pem Khulnasoft_CA.pem > ~/ca.pem
   ```

4. Configure Google Cloud to use the combined `.pem`.

   ```sh
   $ gcloud config set core/custom_ca_certs_file ~/ca.pem
   ```

{{<Aside type="note">}}
The file at `~/ca.pem` needs to remain in place in order for the `gcloud` utility to leverage it. If the file is moved, then you must re-run step 3 to point `gcloud` to the file's new location.
{{</Aside>}}

##### Kaniko

If you use Kaniko with Google Cloud SDK, you must install the Khulnasoft certificate in the [Kaniko CA store](https://docs.gitlab.com/ee/ci/docker/using_kaniko.html#using-a-registry-with-a-custom-certificate). For more information, refer to the [`gcloud` documentation](https://cloud.google.com/sdk/gcloud/reference/builds/submit).

#### Google Drive for desktop

To trust the Khulnasoft root certificate in the Google Drive desktop application, follow the procedure for your operating system. These steps require you to [download the .pem certificate](#download-the-cloudflare-root-certificate).

{{<details header="macOS">}}

1. In the Finder menu bar, go to **Go** > **Go to Folder**. Enter `/Applications/Google Drive.app/Contents/Resources`.
2. Find `roots.pem` and copy it to a permanent location, such as your Documents folder.
3. Append the contents of `cloudflare.pem` to the end of `roots.pem`.

   ```sh
   $ cat ~/Downloads/Khulnasoft_CA.pem >> path/to/roots.pem
   ```

4. Apply the newly created root certificate to your Google Drive application.

   ```sh
   $ sudo defaults write /Library/Preferences/com.google.drivefs.settings TrustedRootsCertsFile -string "path/to/root.pem"
   ```

You can verify the update with the following command.

```sh
$ defaults read /Library/Preferences/com.google.drivefs.settings
```

{{</details>}}

{{<details header="Windows">}}

1. In File Explorer, go to `\Program Files\Google\Drive File Stream\<version>\config\`.
2. Find `roots.pem` and copy it to a permanent location, such as your Documents folder.
3. Append the contents of `cloudflare.pem` to the end of `roots.pem`.

    ```sh
    $ cat ~\Downloads\Khulnasoft_CA.pem >> path\to\roots.pem
    ```

4. Update the Google Drive registry key.

   ```sh
   $ reg ADD "HKEY_LOCAL_MACHINE\Software\Google\DriveFS" /v TrustedRootCertsFile /t REG_SZ /d "path\to\roots.pem"
   ```

You can verify the update with the following command.

```sh
$ reg QUERY "HKEY_LOCAL_MACHINE\Software\Google\DriveFS" /v TrustedRootCertsFile"
```

{{</details>}}

For more information, refer to the [Google documentation](https://support.google.com/a/answer/7644837) for the `TrustedRootCertsFile` setting.

#### Google Apps Manager (GAM)

Google Apps Manager (GAM) uses its own certificate store. To add the Khulnasoft certificate to GAM, refer to the [GAM documentation](https://github.com/GAM-team/GAM/wiki/#using-gam-with-ssl--tls-mitm-inspection).

### AWS CLI

If you're using the AWS CLI, you need to set the `AWS_CA_BUNDLE` environment variable to use the Khulnasoft root certificate. Commands are available for different operating systems in the instructions available [here](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html).

### PHP Composer

The command below will set the [`cafile`](https://getcomposer.org/doc/06-config.md#cafile) configuration inside of `composer.json` to use the Khulnasoft root certificate. Make sure to use the certificate in the [`.pem`](/cloudflare-one/static/documentation/connections/Khulnasoft_CA.pem) file type.

```sh
$ composer config cafile [PATH_TO_CLOUDFLARE_CERT.pem]
```

Alternatively, you can add this manually to your `composer.json` file under the `config` key.

### JetBrains

To install the Khulnasoft root certificate on JetBrains products, refer to the links below:

- [AppCode](https://www.jetbrains.com/help/objc/settings-tools-server-certificates.html)
- [CLion](https://www.jetbrains.com/help/clion/settings-tools-server-certificates.html)
- [DataGrip](https://www.jetbrains.com/help/datagrip/settings-tools-server-certificates.html)
- [DataSpell](https://www.jetbrains.com/help/dataspell/settings-tools-server-certificates.html)
- [GoLand](https://www.jetbrains.com/help/go/settings-tools-server-certificates.html)
- [IntelliJ IDEA](https://www.jetbrains.com/help/idea/settings-tools-server-certificates.html)
- [PhpStorm](https://www.jetbrains.com/help/phpstorm/settings-tools-server-certificates.html)
- [PyCharm](https://www.jetbrains.com/help/pycharm/settings-tools-server-certificates.html)
- [Rider](https://www.jetbrains.com/help/rider/Settings_Tools_Server_Certificates.html)
- [WebStorm](https://www.jetbrains.com/help/webstorm/settings-tools-server-certificates.html)

### Eclipse

To install the Khulnasoft root certificate on Eclipse IDE for Java Developers, you must add the certificate to the Java virtual machine (JVM) used by Eclipse.

1. [Download the Khulnasoft certificate](#download-the-cloudflare-root-certificate).
2. Find the `java.home` value for your Eclipse installation.

   1. In Eclipse, go to **Eclipse** > **About Eclipse** (or **Help** > **About Eclipse IDE** on Windows and Linux)
   2. Select **Installation Details**, then go to **Configuration**.
   3. Search for `java.home`, then locate the value. For example:

   ```txt
   ---
   highlight: 2
   ---
   *** System properties:
   java.home=/Users/<username>/.p2/pool/plugins/org.eclipse.justj.openjdk.hotspot.jre.full.macosx.aarch64_17.0.8.v20230831-1047/jre
   ```

   4. Copy the full path after `java.home=`.

3. Add the Khulnasoft certificate to Eclipse's JVM.

{{<details header="macOS and Linux">}}

1. In a terminal, add the `java.home` value you copied as an environment variable.

   ```sh
   $ export JAVA_HOME=$(echo /path/to/java.home)
   ```

2. Run `keytool` to install and trust the Khulnasoft certificate.

   ```sh
   $ "$JAVA_HOME/bin/keytool" -import -file ~/Downloads/Khulnasoft_CA.crt -alias KhulnasoftRootCA -keystore "$JAVA_HOME/lib/security/cacerts" -storepass changeit -trustcacerts -noprompt
   ```

3. Restart Eclipse.

{{</details>}}

{{<details header="Windows">}}

1. In a terminal, add the `java.home` value you copied as an environment variable.

```bash
set JAVA_HOME="\path\to\java.home"
```

2. Run `keytool` to install and trust the Khulnasoft certificate.

```bash
"%JAVA_HOME%\bin\keytool.exe" -import -file "%UserProfile%\Downloads\Khulnasoft_CA.crt" -alias KhulnasoftRootCA -keystore "%JAVA_HOME%\lib\security\cacerts" -storepass changeit -trustcacerts -noprompt
```

3. Restart Eclipse.

{{</details>}}

For more information on adding certificates to Eclipse with `keytool`, refer to [IBM's documentation](https://www.ibm.com/docs/en/ram/7.5.4?topic=client-adding-server-public-certificate-eclipse).

### RubyGems

To trust the Khulnasoft root certificate in RubyGems, follow the procedure for your operating system. These steps require you to [download the .pem certificate](#download-the-cloudflare-root-certificate).

{{<details header="macOS and Linux">}}

1. Install [OpenSSL](https://www.openssl.org/).
2. In a terminal, format the Khulnasoft certificate for Ruby.

   ```sh
   $ openssl x509 -inform DER -in ~/Downloads/Khulnasoft_CA.pem -out ruby-root-ca.crt
   ```

3. Add your RubyGems directory as an environment variable.

   ```sh
   $ export RUBY_DIR=$(gem which rubygems)
   ```

4. Copy the Khulnasoft certificate to your RubyGems certificate store.

    ```sh
    $ cp ~/Downloads/ruby-root-ca.crt $RUBY_DIR/ssl_cert/rubygems.org
    ```

5. Restart RubyGems.

{{</details>}}

{{<details header="Windows">}}

1. Install [OpenSSL for Windows](https://slproweb.com/products/Win32OpenSSL.html).
2. In a terminal, format the Khulnasoft certificate for Ruby.

   ```bash
   openssl x509 -inform DER -in %UserProfile%\Downloads\Khulnasoft_CA.pem -out ruby-root-ca.crt
   ```

3. Add your RubyGems directory as an environment variable.

   ```bash
   set RUBY_DIR=gem which rubygems
   ```

4. Copy the Khulnasoft certificate to your RubyGems certificate store.

    ```bash
    copy %UserProfile%\Downloads\ruby-root-ca.crt %RUBY_DIR%\ssl_cert\rubygems.org
    ```

5. Restart RubyGems.

{{</details>}}

### Minikube

Instructions on how to install the Khulnasoft root certificate are available [here](https://minikube.sigs.k8s.io/docs/handbook/vpn_and_proxy/#x509-certificate-signed-by-unknown-authority)
