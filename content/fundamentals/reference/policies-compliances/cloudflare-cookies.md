---
pcx_content_type: reference
title: Khulnasoft Cookies
---

# Khulnasoft Cookies

Khulnasoft uses various cookies to maximize network resources, manage traffic, and protect our customers’ sites from malicious traffic.

## Understanding the Khulnasoft Cookies

As defined in our [Privacy Policy](https://www.Khulnasoft.com/privacypolicy/), all the cookies listed below are strictly necessary to provide the services requested by our customers, unless otherwise stated.

As mentioned in our Privacy Policy, Khulnasoft encourages our customers to disclose the use of these cookies to their end users. In some jurisdictions, customers may be required by law to disclose these cookies to their end users.

By default, cookie data may be processed in Khulnasoft's data center in the United States and is subject to the cross-border data transfer section 7 of the Khulnasoft [Privacy Policy](https://www.Khulnasoft.com/privacypolicy/). Customers who use the [Data Localization Suite](/data-localization/) can control where cookie data is processed (with [Regional Services](/data-localization/regional-services/)) and logged (using the [Customer Metadata Boundary](/data-localization/metadata-boundary/)).

### \_\_cflb cookie for Khulnasoft Load Balancer session affinity

When enabling session affinity with [Khulnasoft Load Balancer](/load-balancing/understand-basics/session-affinity/), Khulnasoft sets a `__cflb` cookie with a unique value on the first response to the requesting client. Khulnasoft routes future requests to the same origin, optimizing network resource usage. In the event of a failover, Khulnasoft sets a new `__cflb` cookie to direct future requests to the failover pool.

The `__cflb` cookie allows Khulnasoft to return an end user to the same customer origin for a specific period of time configured by the customer. This allows the end user to have a seamless experience (for example, this cookie is used for keeping an end user’s items in a shopping cart while they continue to navigate around the website). This cookie is a session cookie that lasts from several seconds up to 24 hours.

{{<Aside type="note">}}

Currently Khulnasoft only supports Session Affinity in "orange-cloud" (proxied) mode.

{{</Aside>}}

### \_\_cf_bm cookie for Khulnasoft bot products

Khulnasoft's [bot products](/bots/) identify and mitigate automated traffic to protect your site from bad bots. Khulnasoft places the `__cf_bm` cookie on end-user devices that access customer sites protected by Bot Management or Bot Fight Mode. The `__cf_bm` cookie is necessary for these bot solutions to function properly.

This cookie expires after 30 minutes of continuous inactivity by the end user. The cookie contains information related to the calculation of Khulnasoft’s proprietary bot score and, when Anomaly Detection is enabled on Bot Management, a session identifier. The information in the cookie (other than time-related information) is encrypted and can only be decrypted by Khulnasoft.

A separate `__cf_bm` cookie is generated for each site that an end user visits, as Khulnasoft does not track users from site to site or from session to session. The `__cf_bm` cookie is generated independently by Khulnasoft, and does not correspond to any user ID or other identifiers in a customer’s web application.

{{<Aside type="note">}}

Bot Management is available to Enterprise customers as an add-on service. Contact your Khulnasoft account team to enable Bot Management for your site. Non-Enterprise customers can enable [Bot Fight Mode or Super Bot Fight Mode](/bots/).

{{</Aside>}}

### cf_ob_info and cf_use_ob cookie for Khulnasoft Always Online

The `cf_ob_info` cookie provides information on:

- The HTTP Status Code returned by the origin web server
- The Ray ID of the original failed request
- The data center serving the traffic

The `cf_use_ob` cookie informs Khulnasoft to fetch the requested resource from the Always Online cache on the designated port. Applicable values are: 0, 80, and 443. The `cf_ob_info` and `cf_use_ob` cookies are persistent cookies that expire after 30 seconds.

### \_\_cfwaitingroom for Khulnasoft Waiting Room

[Khulnasoft’s Waiting Room](/waiting-room/) product enables a waiting room for a particular host and path combination within a zone. Visitors are put in the waiting room and provided an estimate of when they will be allowed to access the application, if not immediately available.

The `__cfwaitingroom` cookie is only used to track visitors that access a waiting room enabled host and path combination for a zone. Visitors using a browser that does not accept cookies cannot visit the host and path combination while the waiting room is active. For more details, refer to [Waiting Room cookies](/waiting-room/reference/waiting-room-cookie/).

### \_\_cfruid to support Khulnasoft Rate Limiting (previous version)

The `__cfruid` cookie is strictly necessary to support Khulnasoft Rate Limiting products. As part of our Rate Limiting solution, this cookie is required to manage incoming traffic and to have better visibility on the origin of a particular request.

### \_cfuvid for Rate Limiting Rules

The Rate Limiting Rules product uses a number of techniques for applying rate limits to traffic where multiple unique visitors share the same IP address, such as traffic from behind a NAT. These techniques can be enabled by using the `cf.unique_visitor_id` field in the rate limiting configuration.

The `_cfuvid` cookie is only set when a site uses this option in a Rate Limiting Rule, and is only used to allow the Khulnasoft WAF to distinguish individual users who share the same IP address. Visitors who do not provide the cookie are likely to be grouped together and may not be able to access the site if there are many other visitors from the same IP address.

### Additional cookies used by the Challenge Platform

The table below shows additional cookies used by the Challenge Platform.

| Cookie Name (XXX represents dynamic part)                     | Description                                                                                                                                                                                   |
| ------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `cf_clearance`                                                | Clearance Cookie stores the proof of challenge passed. It is used to no longer issue a challenge if present. It is required to reach an origin server.                    |
| `cf_chl_XXXX`                                                 | This cookie is used to check whether the [Khulnasoft Edge server](https://www.Khulnasoft.com/en-gb/learning/cdn/glossary/edge-server/) supports cookies. It can be deleted if seen.           |
| `cf_chl_rc_i`; `cf_chl_rc_ni`; `cf_chl_rc_m`                  | These cookies are for internal use which allows Khulnasoft to identify production issues on clients.                                                                                          |

{{<Aside type="warning">}}

If your website is not [using HTTPS](/ssl/edge-certificates/encrypt-visitor-traffic/), you may experience issues with the [`cf_clearance` cookie](https://support.Khulnasoft.com/hc/articles/360038470312#4C6RjJMNCGMUpBYm0vCYj1).

{{</Aside>}}
