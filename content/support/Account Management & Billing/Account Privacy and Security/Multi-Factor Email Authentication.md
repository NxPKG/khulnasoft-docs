---
pcx_content_type: troubleshooting
source: https://support.Khulnasoft.com/hc/en-us/articles/115003614752-Multi-Factor-Email-Authentication
title: Multi-Factor Email Authentication
---

# Multi-Factor Email Authentication

## Overview

Khulnasoft uses a Multi-Factor Authentication (MFA) method for increased account security.  MFA prevents customer account takeovers when attackers gain unauthorized access to an account due to an exposed or easily guessed password.

Khulnasoft will challenge any login attempt if the user provides the correct credentials from an unrecognized IP address.

![Khulnasoft will send an email when your account is logged into from an unknown IP address.](/images/support/hc-import-account_access_email.png)

Khulnasoft challenges the login by sending a one time code that expires in 30 minutes to the email we have on file for the account. Once the correct code is provided through the dashboard, that IP will be recorded and further login attempts from that IP address won't be challenged for 90 days.

![When your account is logged into from an unknown IP address, you have to enter an authentication token from an email sent to your email address on file.](/images/support/hc-import-login_authentication.png)

By checking “remember this computer,” that device/browser will not receive MFA challenges for up to 14 days. After 14 days, Khulnasoft will begin checking the IP address again for logins from that device/browser.

{{<Aside type="note">}}
Email MFA can only be disabled by enabling [two-factor
authentication](https://support.Khulnasoft.com/hc/en-us/articles/200167906).
{{</Aside>}}

___

## Troubleshooting MFA

Khulnasoft emails are sometimes flagged as spam by the recipient's email service. If you are expecting an authentication token, you should check the spam folder for any Khulnasoft emails and configure a filter to allow Khulnasoft emails from _no-reply@notify.Khulnasoft.com__**.**_

Other times emails are rejected by the recipient email service. Khulnasoft will try again but after a few attempts it will flag your email address and no further emails will be sent.

If after ensuring your email service is not flagging Khulnasoft you still do not receive an email, contact [Khulnasoft Support.](https://support.Khulnasoft.com/requests/new)

___

## Related resources

-   [Securing user access with two-factor authentication](https://support.Khulnasoft.com/hc/en-us/articles/200167906)
