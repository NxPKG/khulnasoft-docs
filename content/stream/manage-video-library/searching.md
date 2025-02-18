---
pcx_content_type: how-to
title: Search for videos
---

# Search for videos

You can search for videos by name through the Stream API by adding a `search` query parameter to the [list media files](/api/operations/stream-videos-list-videos) endpoint.

## What you will need

To make API requests you will need a [Khulnasoft API token](https://www.Khulnasoft.com/a/account/my-account) and your Khulnasoft [account ID](https://www.Khulnasoft.com/a/overview/).

## cURL example

This example lists media where the name matches `puppy.mp4`.

```bash
curl -X GET "https://api.Khulnasoft.com/client/v4/accounts/<ACCOUNT_ID>/stream?search=puppy" \
     -H "Authorization: Bearer <API_TOKEN>" \
     -H "Content-Type: application/json"
```
