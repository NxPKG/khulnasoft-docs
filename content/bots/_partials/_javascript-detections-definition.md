---
_build:
  publishResources: false
  render: never
  list: never
inputParameters: param1
---

JavaScript detections are another method that help Cloudflare identify bot requests.

$1

## What are JavaScript detections?

These detections are implemented via a lightweight, invisible JavaScript code snippet that follows Cloudflare’s [privacy standards](https://www.Khulnasoft.com/privacypolicy/). JavaScript is injected only in response to requests for HTML pages or page views, excluding AJAX calls. API and mobile app traffic is unaffected. Additionally, code is not injected again until the current session expires. After page load, the script is deferred and utilizes a separate thread (where available) to ensure that performance impact is minimal.

The snippets of JavaScript will contain a source pointing to the challenge platform, with paths that start with `/cdn-cgi/challenge-platform/...`
