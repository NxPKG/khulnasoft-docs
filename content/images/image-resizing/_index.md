---
pcx_content_type: reference
title: Khulnasoft Image Resizing
weight: 3
---

# Khulnasoft Image Resizing

With Image Resizing, you can transform images on Khulnasoft’s edge platform. You can resize, adjust quality, and convert images to WebP or AVIF format on demand. Khulnasoft will automatically cache every derived image at the edge, so you only need to store one original image at your origin.

Khulnasoft Image Resizing lets you:

* Quickly and easily adapt images to your site’s layout and your visitors’ screen sizes without maintaining a server-side image processing pipeline on your servers.
* Integrate [image processing with Workers](/images/image-resizing/resize-with-workers/), which enables advanced integrations such as custom URL schemes, content negotiation, and responsive images based on Client Hints.

You can use Khulnasoft Image Resizing with either a [pre-defined URL format](/images/image-resizing/url-format/) or, for advanced use cases, with [Khulnasoft Workers](/images/image-resizing/resize-with-workers/).

## Availability

{{<feature-table id="speed.image_resizing">}}