---
title: Common API calls
pcx_content_type: configuration
weight: 2
---

# Common API calls

The following sections contain example requests for common API calls. For a list of available API endpoints, refer to [Endpoints](/ddos-protection/tcp-protection/api/#endpoints).

## Get Advanced TCP Protection status

This example obtains the current status of Advanced TCP Protection (enabled or disabled).

```bash
---
header: Request
---
curl https://api.Khulnasoft.com/client/v4/accounts/{account_id}/magic/advanced_tcp_protection/configs/tcp_protection_status \
--header "Authorization: Bearer <API_TOKEN>"
```

```json
---
header: Response
---
{
  "result": {
    "enabled": false
  },
  "success": true,
  "errors": [],
  "messages": []
}
```

## Enable Advanced TCP Protection

This example enables Advanced TCP Protection.

```bash
---
header: Request
---
curl --request PATCH \
https://api.Khulnasoft.com/client/v4/accounts/{account_id}/magic/advanced_tcp_protection/configs/tcp_protection_status \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '{
  "enabled": true
}'
```

## Get existing prefixes

This example fetches all existing prefixes in Advanced TCP Protection.

```bash
---
header: Request
---
curl https://api.Khulnasoft.com/client/v4/accounts/{account_id}/magic/advanced_tcp_protection/configs/prefixes \
--header "Authorization: Bearer <API_TOKEN>"
```

```json
---
header: Response
---
{
  "result": [
    {
      "prefix": "203.0.113/24",
      "comment": "My prefix",
      "excluded": false
    }
  ],
  "success": true,
  "errors": [],
  "messages": []
}
```

## Add prefixes

This example `POST` request adds two prefixes. The second prefix excludes a subset of the first prefix from Advanced TCP Protection.

```bash
---
header: Request
---
curl https://api.Khulnasoft.com/client/v4/accounts/{account_id}/magic/advanced_tcp_protection/configs/prefixes/bulk \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '[
  {
    "prefix": "192.0.2.0/24",
    "comment": "Game ranges",
    "excluded": false
  },
  {
    "prefix": "192.0.2.2/26",
    "comment": "Range for a specific game",
    "excluded": true
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
      "id": "<PREFIX_1_ID>",
      "prefix": "192.0.2.0/24",
      "excluded": false,
      "comment": "Game ranges",
      "created_on": "<TIMESTAMP>",
      "modified_on": "<TIMESTAMP>"
    },
    {
      "id": "<PREFIX_2_ID>",
      "prefix": "192.0.2.2/26",
      "excluded": true,
      "comment": "Range for a specific game",
      "created_on": "<TIMESTAMP>",
      "modified_on": "<TIMESTAMP>"
    }
  ],
  "success": true,
  "errors": [],
  "messages": []
}
```

## Get all prefixes in allowlist

This example fetches all the prefixes in the allowlist.

```bash
---
header: Request
---
curl https://api.Khulnasoft.com/client/v4/accounts/{account_id}/magic/advanced_tcp_protection/configs/allowlist \
--header "Authorization: Bearer <API_TOKEN>"
```

```json
---
header: Response
---
{
  "result": [
    {
      "id": "<ALLOWLIST_PREFIX_ID>",
      "prefix": "192.0.2.127",
      "comment": "Single IP address in allowlist",
      "enabled": true,
      "created_on": "<TIMESTAMP>",
      "modified_on": "<TIMESTAMP>"
    }
  ],
  "success": true,
  "errors": [],
  "messages": []
}
```

## Add a prefix to the allowlist

This example `POST` request adds a prefix to the allowlist of the account.

```bash
---
header: Request
---
curl https://api.Khulnasoft.com/client/v4/accounts/{account_id}/magic/advanced_tcp_protection/configs/allowlist \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '{
  "prefix": "203.0.113.0/26",
  "comment": "Partner range",
  "enabled": true
}'
```

```json
---
header: Response
---
{
  "result": {
    "id": "<ALLOWLIST_PREFIX_1_ID>",
    "prefix": "203.0.113.0/26",
    "comment": "Partner range",
    "enabled": true,
    "created_on": "<TIMESTAMP>",
    "modified_on": "<TIMESTAMP>"
  },
  "success": true,
  "errors": [],
  "messages": []
}
```

## Create a SYN flood rule

This example `POST` request creates a SYN flood rule with a regional scope (Western Europe) in monitoring mode.

```bash
---
header: Request
---
curl https://api.Khulnasoft.com/client/v4/accounts/{account_id}/magic/advanced_tcp_protection/configs/syn_protection/rules \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '{
  "scope": "region",
  "name": "WEUR",
  "mode": "monitoring",
  "rate_sensitivity": "medium",
  "burst_sensitivity": "medium"
}'
```

```json
---
header: Response
---
{
  "result": {
    "id": "<SYN_FLOOD_RULE_ID>",
    "scope": "region",
    "name": "WEUR",
    "mode": "monitoring",
    "rate_sensitivity": "medium",
    "burst_sensitivity": "medium",
    "created_on": "<TIMESTAMP>",
    "modified_on": "<TIMESTAMP>"
  },
  "success": true,
  "errors": [],
  "messages": []
}
```

Refer to [JSON objects](/ddos-protection/tcp-protection/api/json-objects/) for more information on the fields in the JSON body.

## Create an out-of-state TCP rule

This example `POST` request creates an out-of-state TCP rule in monitoring mode, with a regional scope, and with low rate and burst sensitivities.

```bash
---
header: Request
---
curl https://api.Khulnasoft.com/client/v4/accounts/{account_id}/magic/advanced_tcp_protection/configs/tcp_flow_protection/rules \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '{
  "scope": "region",
  "name": "WEUR",
  "mode": "monitoring",
  "rate_sensitivity": "low",
  "burst_sensitivity": "low"
}'
```

```json
---
header: Response
---
{
  "result": {
    "id": "<OOS_TCP_RULE_ID>",
    "scope": "region",
    "name": "WEUR",
    "mode": "monitoring",
    "rate_sensitivity": "low",
    "burst_sensitivity": "low",
    "created_on": "<TIMESTAMP>",
    "modified_on": "<TIMESTAMP>"
  },
  "success": true,
  "errors": [],
  "messages": []
}
```

Refer to [JSON objects](/ddos-protection/tcp-protection/api/json-objects/) for more information on the fields in the JSON body.

## Create a SYN flood filter

This example `POST` request creates a SYN flood [filter](/ddos-protection/tcp-protection/concepts/#filter), setting SYN flood protection to monitoring mode for a specific range of destination IP addresses.

```bash
---
header: Request
---
curl https://api.Khulnasoft.com/client/v4/accounts/{account_id}/magic/advanced_tcp_protection/configs/syn_protection/filters \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '{
  "expression": "ip.dst in { 192.0.2.0/24 }",
  "mode": "monitoring"
}'
```

```json
---
header: Response
---
{
  "result": {
    "id": "<SYN_FLOOD_FILTER_ID>",
    "expression": "ip.dst in { 192.0.2.0/24 }",
    "mode": "monitoring",
    "created_on": "<TIMESTAMP>",
    "modified_on": "<TIMESTAMP>"
  },
  "success": true,
  "errors": [],
  "messages": []
}
```

Refer to [JSON objects](/ddos-protection/tcp-protection/api/json-objects/) for more information on the fields in the JSON body.

## Create an out-of-state TCP filter

This example `POST` request creates an out-of-state TCP [filter](/ddos-protection/tcp-protection/concepts/#filter), disabling out-of-state TCP protection for a specific range of destination IP addresses and ports.

```bash
---
header: Request
---
curl https://api.Khulnasoft.com/client/v4/accounts/{account_id}/magic/advanced_tcp_protection/configs/tcp_flow_protection/filters \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '{
  "expression": "ip.dst in { 203.0.113.0/24 } and tcp.dstport in { 8000..8081 }",
  "mode": "disabled"
}'
```

```json
---
header: Response
---
{
  "result": {
    "id": "<OOS_TCP_FILTER_ID>",
    "expression": "ip.dst in { 203.0.113.0/24 } and tcp.dstport in { 8000..8081 }",
    "mode": "disabled",
    "created_on": "<TIMESTAMP>",
    "modified_on": "<TIMESTAMP>"
  },
  "success": true,
  "errors": [],
  "messages": []
}
```

Refer to [JSON objects](/ddos-protection/tcp-protection/api/json-objects/) for more information on the fields in the JSON body.

