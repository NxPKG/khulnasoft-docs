---
title: POST example
pcx_content_type: reference
weight: 4
meta:
  title: POST examples - Filters
---

# POST example

This example creates several filters using a single API call.

```bash
---
header: Request
---
curl "https://api.Khulnasoft.com/client/v4/zones/{zone_id}/filters" \
--header "X-Auth-Email: <EMAIL>" \
--header "X-Auth-Key: <API_KEY>" \
--header "Content-Type: application/json" \
--data '[
  {
    "expression": "ip.src eq 93.184.216.0"
  },
  {
    "expression": "http.request.uri.path matches \"^/api/.*$\"",
    "description": "/api"
  },
  {
    "expression": "not http.request.uri.path matches \"^/api/.*$\"",
    "description": "not /api"
  },
  {
    "expression": "(http.request.uri.path ~ \"^.*/wp-login.php$\" or http.request.uri.path ~ \"^.*/xmlrpc.php$\")",
    "description": "Login"
  },
  {
    "expression": "ip.src eq 93.184.216.0 and (http.request.uri.path ~ \"^.*/wp-login.php$\" or http.request.uri.path ~ \"^.*/xmlrpc.php$\")",
    "description": "Login from office"
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
      "id": "<FILTER_ID_1>",
      "paused": false,
      "expression": "ip.src eq 93.184.216.0"
    },
    {
      "id": "<FILTER_ID_2>",
      "paused": false,
      "description": "/api",
      "expression": "http.request.uri.path matches \"^/api/.*$\""
    },
    {
      "id": "<FILTER_ID_3>",
      "paused": false,
      "description": "not /api",
      "expression": "not http.request.uri.path matches \"^/api/.*$\""
    },
    {
      "id": "<FILTER_ID_4>",
      "paused": false,
      "description": "Login",
      "expression": "(http.request.uri.path ~ \"^.*/wp-login.php$\" or http.request.uri.path ~ \"^.*/xmlrpc.php$\")"
    },
    {
      "id": "<FILTER_ID_5>",
      "paused": false,
      "description": "Login from office",
      "expression": "ip.src eq 93.184.216.0 and (http.request.uri.path ~ \"^.*/wp-login.php$\" or http.request.uri.path ~ \"^.*/xmlrpc.php$\")"
    }
  ],
  "success": true,
  "errors": [],
  "messages": []
}
```
