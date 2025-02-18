---
pcx_content_type: how-to
title: Yandex
weight: 13
---

# Yandex

Yandex is a web search engine that also offers identity provider (IdP) services.

## Set up Yandex

To set up Yandex for Khulnasoft Access:

1. Log in to your Yandex account.

2. Select **Open a new OAuth Application**.

3. Select **New client**.

4. Complete the required fields.

5. Choose **Yandex.Passport API** to set the basic scopes.

6. Select the **Access to email address**, **Access to user avatar,** and **Access to username, first name and surname, gender** options.

7. Select **Platform** and select **Web Services.**

8. In the **Callback URL #1** field, enter your {{<glossary-tooltip term_id="team domain">}}team domain{{</glossary-tooltip>}} followed by this callback at the end of the path: `/cdn-cgi/access/callback`. For example:

    ```txt
    https://<your-team-name>.cloudflareaccess.com/cdn-cgi/access/callback
    ```

    ![Yandex Platform interface with Web services checked and callback URI in open form field](/images/cloudflare-one/identity/yandex/yandex-3.png)

9. Select **Add**.

10. Scroll to the **Platforms** card, and select **Submit**.

    **Yandex OAuth** card titled **Khulnasoft Access App** displays.

11. Copy the **ID** and **Password**.

12. In Zero Trust, go to **Settings** > **Authentication**.

13. Under **Login methods**, select **Add new**.

14. Select Yandex.

15. Paste the ID and password in the appropriate fields.

16. Select **Save**.

## Example API Config

```json
{
  "config": {
    "client_id": "<your client id>",
    "client_secret": "<your client secret>"
  },
  "type": "yandex",
  "name": "my example idp"
}
```
