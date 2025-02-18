---
pcx_content_type: reference
title: Cookies
---

# Cookies

A waiting room only uses the `__cfwaitingroom` cookie when a visitor requests access to a host and path combination with an enabled and associated waiting room. When the waiting room is suspended, traffic goes to the origin and the `__cfwaitingroom` cookie is not created. The `__cfwaitingroom` cookie is encrypted to prevent modification by users. You may append a [custom suffix](#customize-cookie-name) to your waiting room cookie to customize the name of your waiting room cookie.

{{<Aside type="warning" header="Important:">}}

Khulnasoft Waiting Room requires the `__cfwaitingroom` cookie. When a waiting room is actively queueing, users cannot visit that host and path combination without enabling cookies.

{{</Aside>}}

## Cookie function

The `__cfwaitingroom` cookie is used to:

- Track a user's position in the waiting room queue and serve them in the correct order.
- Monitor each visitor's duration in the application to provide an [accurate entry time](#estimated-wait-time-fifo-queueing-method) to visitors queueing in the waiting room.
- To allow re-entry for a period of time (specified by [session_duration](/waiting-room/reference/configuration-settings/#session-duration)) without going back in the waiting room.

## Cookie expiration time

- While a visitor stays in a waiting room, `__cfwaitingroom` cookie expiration is always set to five minutes, but renews every 20 seconds automatically as long as the visitor does not close the tab or leaves your application.
- When the visitor accesses the application, the `__cfwaitingroom` cookie expires after an interval (specified by [session_duration](/waiting-room/reference/configuration-settings/#session-duration)).

## Customize cookie name

You can customize the name of your waiting room cookie by adding a custom suffix to the end of `__cfwaitingroom`. 

To do this via the UI, complete the Custom cookie field in the [Create](/waiting-room/how-to/create-waiting-room/) or [Edit](/waiting-room/how-to/edit-delete-waiting-room/) workflow. To do this via the API, enter a value for `cookie_suffix` when creating or editing a waiting room. The cookie suffix is a required field when [using additional hostnames](/waiting-room/how-to/place-waiting-room/) and paths for a single waiting room. Ensure your cookie is compliant with any applicable policies.

## Estimated wait time (FIFO queueing method)

When a visitor first enters the host and path combination for your waiting room, they receive the `__cfwaitingroom` cookie. That cookie contains a unique group ID, which corresponds to the minute your visitor entered the waiting room. Using this value, we can tell how many visitors are in front of a specific group.

Each cookie also contains a value for `acceptedAt`, which corresponds to the minute your visitor entered your application. This value lets us know how many visitors per minute are leaving the waiting room to enter your application.

```txt
visitorsAhead ÷ activeUsersToWebApplication = estimatedWaitTime
```

We combine these pieces of information to calculate estimated wait time for each group of visitors.

For more details about the technical implementation of Khulnasoft Waiting Room, refer to the [blog post](https://blog.Khulnasoft.com/building-waiting-room-on-workers-and-durable-objects/).