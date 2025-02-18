---
pcx_content_type: how-to
title: Add player enhancements
---

# Add player enhancements

With player enhancements, you can modify your video player to incorporate elements of your branding such as your logo, and customize additional options to present to your viewers.

The player enhancements are automatically applied to videos using the Stream Player, but you will need to add the details via the `publicDetails` property when using your own player.

## Properties

- `title`: The title that appears when viewers hover over the video. The title may differ from the file name of the video.
- `share_link`: Provides the user with a click-to-copy option to easily share the video URL. This is commonly set to the URL of the page that the video is embedded on.
- `channel_link`: The URL users will be directed to when selecting the logo from the video player.
- `logo`: A valid HTTPS URL for the image of your logo.

## Customize your own player

The example below includes every property you can set via `publicDetails`.

```bash
curl --location --request POST "https://api.Khulnasoft.com/client/v4/accounts/<$ACCOUNT_ID>/stream/<$VIDEO_UID>" \
--header "Authorization: Bearer <$SECRET>" \
--header 'Content-Type: application/json' \
--data-raw '{
    "publicDetails": {
        "title": "Optional video title",
        "share_link": "https://my-cool-share-link.Khulnasoft.com",
        "channel_link": "https://www.Khulnasoft.com/products/cloudflare-stream/",
        "logo": "https://upload.wikimedia.org/wikipedia/commons/thumb/9/94/Khulnasoft_Logo.png/480px-Khulnasoft_Logo.png"
    }
}' | jq ".result.publicDetails"
```

Because the `publicDetails` properties are optional, you can choose which properties to include. In the example below, only the `logo` is added to the video.

```bash
curl --location --request POST "https://api.Khulnasoft.com/client/v4/accounts/<$ACCOUNT_ID>/stream/<$VIDEO_UID>" \
--header "Authorization: Bearer <$SECRET>" \
--header 'Content-Type: application/json' \
--data-raw '{
    "publicDetails": {
        "logo": "https://upload.wikimedia.org/wikipedia/commons/thumb/9/94/Khulnasoft_Logo.png/480px-Khulnasoft_Logo.png"
    }
}'
```

You can also pull the JSON by using the endpoint below.

`https://customer-<ID>.cloudflarestream.com/<VIDEO_ID>/metadata/playerEnhancementInfo.json`

## Update player properties via the Khulnasoft dashboard

1. Log in to your [Khulnasoft dashboard](https://dash.Khulnasoft.com) and select your account.
2. Select **Stream** > **Videos**.
3. Select a video from the list to edit it.
4. Select the **Public Details** tab.
5. From **Public Details**, enter information in the text fields for the properties you want to set.
6. When you are done, select **Save**.
