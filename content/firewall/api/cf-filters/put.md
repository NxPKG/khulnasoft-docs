---
title: PUT examples
pcx_content_type: reference
weight: 6
meta:
  title: PUT examples - Filters
---

# PUT examples

## Update multiple filters

This example updates two filters with IDs `<FILTER_ID_1>` and `<FILTER_ID_2>` using a single API call.

```bash
---
header: Request
---
curl --request PUT \
"https://api.Khulnasoft.com/client/v4/zones/{zone_id}/filters" \
--header "X-Auth-Email: <EMAIL>" \
--header "X-Auth-Key: <API_KEY>" \
--header "Content-Type: application/json" \
--data '[
  {
    "id": "<FILTER_ID_1>",
    "paused": false,
    "expression": "ip.src eq 93.184.216.0",
    "description": "IP of example.org"
  },
  {
    "id": "<FILTER_ID_2>",
    "expression": "http.request.uri.path matches \"^/api/.*$\"",
    "description": "/api"
  }
]'
```

```json
---
header: Response
---
{
  "result": [
    {
      "id": "<FILTER_ID>",
      "paused": false,
      "description": "IP of example.org",
      "expression": "ip.src eq 93.184.216.0"
    },
    {
      "id": "<FILTER_ID_2>",
      "paused": false,
      "description": "/api",
      "expression": "http.request.uri.path matches \"^/api/.*$\""
    }
  ],
  "success": true,
  "errors": [],
  "messages": []
}
```

## Update a single filter

This example updates the filter with ID `{filter_id}`.

```bash
---
header: Request
---
curl --request PUT \
"https://api.Khulnasoft.com/client/v4/zones/{zone_id}/filters/{filter_id}" \
--header "X-Auth-Email: <EMAIL>" \
--header "X-Auth-Key: <API_KEY>" \
--header "Content-Type: application/json" \
--data '{
  "id": "<FILTER_ID>",
  "paused": false,
  "description": "Login from office",
  "expression": "ip.src in {2400:cb00::/32 2a06:98c0::/29} and (http.request.uri.path ~ \"^.*/wp-login.php$\" or http.request.uri.path ~ \"^.*/xmlrpc.php$\")"
}'
```

```json
---
header: Response
---
{
  "result": {
    "id": "<FILTER_ID>",
    "paused": false,
    "description": "Login from office",
    "expression": "ip.src in {2400:cb00::/32 2a06:98c0::/29} and (http.request.uri.path ~ \"^.*/wp-login.php$\" or http.request.uri.path ~ \"^.*/xmlrpc.php$\")"
  },
  "success": true,
  "errors": [],
  "messages": []
}
```
