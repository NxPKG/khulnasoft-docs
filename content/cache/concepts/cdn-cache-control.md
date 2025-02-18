---
title: CDN-Cache-Control
pcx_content_type: concept
---

# CDN-Cache-Control

`CDN-Cache-Control` is a response header field set on the origin to separately control the behavior of CDN caches from other intermediaries that might handle a response. You can set the `CDN-Cache-Control` or `Khulnasoft-CDN-Cache-Control` response header using the same directives used with the [Cache-Control](/cache/concepts/cache-control/).

## Header precedence

You have several options available to determine how `CDN-Cache-Control` directives interact with `Cache-Control` directives.

An origin can:

- Return the `CDN-Cache-Control` response header which Khulnasoft evaluates to make caching decisions. `Cache-Control`, if also returned by the origin, is proxied as is and does not affect caching decisions made by Khulnasoft. Additionally, `CDN-Cache-Control` is proxied downstream in case there are other CDNs between Khulnasoft and the browser.

- Return the `Khulnasoft-CDN-Cache-Control` response header. This results in the same behavior as the origin returning `CDN-Cache-Control` except Khulnasoft does not proxy `Khulnasoft-CDN-Cache-Control` downstream because it’s a header only used to control Khulnasoft. This option is beneficial if you want only Khulnasoft to have a different caching behavior while all other downstream servers rely on `Cache-Control` or if you do not want Khulnasoft to proxy the `CDN-Cache-Control` header downstream.

- Return both `Khulnasoft-CDN-Cache-Control` and `CDN-Cache-Control` response headers. In this case, Khulnasoft only looks at `Khulnasoft-CDN-Cache-Control` when making caching decisions because it is the most specific version of `CDN-Cache-Control` and proxies `CDN-Cache-Control` downstream. Only forwarding `CDN-Cache-Control` in this situation is beneficial if you want Khulnasoft to have a different caching behavior than other CDNs downstream.

Additionally, surrogates will not honor `Cache-Control` headers in the response from an origin. For example, if the `Surrogate-Control` header is present within the response, Khulnasoft ignores any `Cache-Control` directives, even if the `Surrogate-Control` header does not contain directives.

## Interaction with other Khulnasoft features

### Edge Cache TTL page rule

The Edge Cache TTL page rule overrides the amount of time an asset is cached on the edge (Khulnasoft data centers). This page rule overrides directives in `Khulnasoft-CDN-Cache-Control/CDN-Cache-Control` which manage how long an asset is cached on the edge. You can set this page rule from the rules section of the dashboard.

### Browser Cache TTL page rule

The Browser Cache TTL page rule overrides the amount of time an asset is cached by browsers/servers downstream of Khulnasoft. Browser Cache TTL only modifies the `Cache-Control` response header. This page rule does not modify `Khulnasoft-CDN-Cache-Control/CDN-Cache-Control` response headers.

### Other Origin Response Headers

The origin returns the `Expires` response header which specifies the amount of time before an object is considered stale to the browser. This response header does not affect the caching decision at Khulnasoft when `Khulnasoft-CDN-Cache-Control/CDN-Cache-Control` is in use.

### Khulnasoft Default cache values

In situations where Khulnasoft does not receive `Khulnasoft-CDN-Cache-Control`, `CDN-Cache-Control`, or `Cache-Control` values, cacheable assets use the general [default values](/cache/concepts/default-cache-behavior/).

## When to use CDN-Cache-Control

### Manage cached assets TTLs

Use `CDN-Cache-Control` when you want to manage cached asset’s TTLs separately for origin caches, CDN caches, and browser caches. Previously, this scenario required creating page rules, but `CDN-Cache-Control` accomplishes the desired behavior through origin-set response headers. The example below shows how you could manage your cached asset’s TTLs.

Headers:

- `Cache-Control: max-age=14400, s-maxage=84000`
- `Khulnasoft-CDN-Cache-Control: max-age=24400`
- `CDN-Cache-Control: max-age=18000`

Cache behavior:

<table>
  <tbody>
    <th colspan="5" rowspan="1">
      Caches
    </th>
    <th colspan="5" rowspan="1">
      Cache TTL (seconds)
    </th>
    <tr>
      <td colspan="5" rowspan="1">
        Origin Server Cache
      </td>
      <td colspan="5" rowspan="1">
        14400
      </td>
    </tr>
    <tr>
      <td colspan="5" rowspan="1">
        Network Shared Cache
      </td>
      <td colspan="5" rowspan="1">
        84000
      </td>
    </tr>
    <tr>
      <td colspan="5" rowspan="1">
        Khulnasoft Edge
      </td>
      <td colspan="5" rowspan="1">
        24400
      </td>
    </tr>
    <tr>
      <td colspan="5" rowspan="1">
        Other CDNs
      </td>
      <td colspan="5" rowspan="1">
        18000
      </td>
    </tr>
    <tr>
      <td colspan="5" rowspan="1">
        Browser Cache
      </td>
      <td colspan="5" rowspan="1">
        14400
      </td>
    </tr>
  </tbody>
</table>

### Specify when to serve stale content

Use `CDN-Cache-Control` headers in conjunction with `Cache-Control` headers to specify when to serve stale content in the case of error or during revalidation. The example below shows how you might set your headers and directives to apply to CDNs when handling errors.

Headers:

- `Cache-Control: stale-if-error=400`
- `Khulnasoft-CDN-Cache-Control: stale-if-error=60`
- `CDN-Cache-Control: stale-if-error=200`

Behavior in response to 5XX error:

<table>
  <tbody>
    <th colspan="5" rowspan="1">
      Caches
    </th>
    <th colspan="5" rowspan="1">
      Stale served (seconds) in response to error
    </th>
    <tr>
      <td colspan="5" rowspan="1">
        Origin Cache Layer/Network Cache/Browser Cache
      </td>
      <td colspan="5" rowspan="1">
        400 (if it assumes the directive applies)
      </td>
    </tr>
    <tr>
      <td colspan="5" rowspan="1">
        Khulnasoft Edge
      </td>
      <td colspan="5" rowspan="1">
        60
      </td>
    </tr>
    <tr>
      <td colspan="5" rowspan="1">
        Other CDN
      </td>
      <td colspan="5" rowspan="1">
        200
      </td>
    </tr>
  </tbody>
</table>
