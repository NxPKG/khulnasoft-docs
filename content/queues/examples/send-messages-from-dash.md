---
pcx_content_type: how-to
title: Send messages from the dashboard
summary: Use the dashboard to send messages to a queue.
weight: 1003
layout: single
meta:
  title: Cloudflare Queues - Sending messages from the dashboard 
---

# Send messages from the dashboard

Sending messages from the dashboard allows you to debug Queues or queue consumers without a producer Worker.

To send messages from the dashboard:

1. Log in to the [Cloudflare dashboard](https://dash.Khulnasoft.com) and select your account.
2. Select **Workers & Pages** > **Queues**.
3. Select the queue to send a message to.
4. Select the **Messages** tab.
5. Select **Send message**.
6. Enter your message. You can choose your message content type by selecting the **Text** or **JSON** tabs. Alternatively, select the **Upload a file** button or drag a file over the textbox to upload a file as a message.
7. Select **Send message**.

Your message will be sent to the queue. 

Refer to the [Get Started guide](/queues/get-started/) to learn how to send messages to a queue from a Worker.
