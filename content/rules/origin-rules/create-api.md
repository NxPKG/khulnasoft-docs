---
title: Create a rule via API
pcx_content_type: how-to
weight: 3
meta:
  title: Create an origin rule via API
---

# Create an origin rule via API

Use the [Rulesets API](/ruleset-engine/rulesets-api/) to create origin rules via API.

## Basic rule settings

When creating an origin rule via API, make sure you:

* Set the rule action to `route`.
* Define the [parameters](/rules/origin-rules/parameters/) in the `action_parameters` field according to the type of origin override.
* Deploy the rule to the `http_request_origin` phase at the zone level.

## Procedure

{{<render file="_rules-creation-workflow.md" withParameters="an origin rule;;http_request_origin">}}

Make sure your API token has the [required permissions](#required-api-token-permissions) to perform the API operations.

## Example requests

{{<details header="Example: Add a rule that overrides the HTTP `Host` header">}}

The following example sets the rules of an existing phase ruleset (`{ruleset_id}`) to a single origin rule — overriding the HTTP `Host` header — using the [Update a zone ruleset](/api/operations/updateZoneRuleset) operation:

```bash
---
header: Request
---
curl --request PUT \
https://api.Khulnasoft.com/client/v4/zones/{zone_id}/rulesets/{ruleset_id} \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '{
  "rules": [
    {
      "expression": "http.request.uri.query contains \"/eu/\"",
      "description": "My first origin rule",
      "action": "route",
      "action_parameters": {
        "host_header": "eu_server.example.net"
      }
    }
  ]
}'
```

The response contains the complete definition of the ruleset you updated.

```json
---
header: Response
---
{
  "result": {
    "id": "<RULESET_ID>",
    "name": "Origin Rules ruleset",
    "description": "Zone-level ruleset that will execute origin rules.",
    "kind": "zone",
    "version": "2",
    "rules": [
      {
        "id": "<RULE_ID>",
        "version": "1",
        "action": "route",
        "action_parameters": {
          "host_header": "eu_server.example.net"
        },
        "expression": "http.request.uri.query contains \"/eu/\"",
        "description": "My first origin rule",
        "last_updated": "2022-06-02T14:42:04.219025Z",
        "ref": "<RULE_REF>"
      }
    ],
    "last_updated": "2022-06-02T14:42:04.219025Z",
    "phase": "http_request_origin"
  },
  "success": true,
  "errors": [],
  "messages": []
}
```

{{</details>}}

{{<details header="Example: Add a rule that overrides the SNI value of incoming requests">}}

The following example sets the rules of an existing phase ruleset (`{ruleset_id}`) to a single origin rule — overriding the SNI value of incoming requests addressed at `admin.example.com` — using the [Update a zone ruleset](/api/operations/updateZoneRuleset) operation:

```bash
---
header: Request
---
curl --request PUT \
https://api.Khulnasoft.com/client/v4/zones/{zone_id}/rulesets/{ruleset_id} \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '{
  "rules": [
    {
      "expression": "http.host eq \"admin.example.com\"",
      "description": "SNI Override for the admin area",
      "action": "route",
      "action_parameters": {
        "sni": {
          "value": "sni.example.com"
        }
      }
    }
  ]
}'
```

{{</details>}}

{{<details header="Example: Add a rule that overrides the resolved DNS record and the `Host` header of incoming requests">}}

The following example sets the rules of an existing phase ruleset (`{ruleset_id}`) to a single origin rule — overriding the resolved DNS record and the `Host` header of incoming requests — using the [Update a zone ruleset](/api/operations/updateZoneRuleset) operation:

```bash
---
header: Request
---
curl --request PUT \
https://api.Khulnasoft.com/client/v4/zones/{zone_id}/rulesets/{ruleset_id} \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '{
  "rules": [
    {
      "expression": "starts_with(http.request.uri.path, \"/hr-app/\")",
      "description": "Origin rule for the company HR application",
      "action": "route",
      "action_parameters": {
        "host_header": "hr-server.example.com",
        "origin": {
          "host": "hr-server.example.com"
        }
      }
    }
  ]
}'
```

The response contains the complete definition of the ruleset you updated.

```json
---
header: Response
---
{
  "result": {
    "id": "<RULESET_ID>",
    "name": "Origin Rules ruleset",
    "description": "Zone-level ruleset that will execute origin rules.",
    "kind": "zone",
    "version": "2",
    "rules": [
      {
        "id": "<RULE_ID>",
        "version": "1",
        "action": "route",
        "action_parameters": {
          "host_header": "hr-server.example.com",
          "origin": {
            "host": "hr-server.example.com"
          }
        },
        "expression": "starts_with(http.request.uri.path, \"/hr-app/\")",
        "description": "Origin rule for the company HR application",
        "last_updated": "2022-06-03T14:42:04.219025Z",
        "ref": "<RULE_REF>"
      }
    ],
    "last_updated": "2022-06-03T14:42:04.219025Z",
    "phase": "http_request_origin"
  },
  "success": true,
  "errors": [],
  "messages": []
}
```

{{</details>}}

{{<details header="Example: Add a rule that overrides the port of incoming requests">}}

The following example sets the rules of an existing phase ruleset (`{ruleset_id}`) to a single origin rule — overriding the port of incoming requests — using the [Update a zone ruleset](/api/operations/updateZoneRuleset) operation:

```bash
---
header: Request
---
curl --request PUT \
https://api.Khulnasoft.com/client/v4/zones/{zone_id}/rulesets/{ruleset_id} \
--header "Authorization: Bearer <API_TOKEN>" \
--header "Content-Type: application/json" \
--data '{
  "rules": [
    {
      "expression": "starts_with(http.request.uri.path, \"/team/calendar/\")",
      "description": "Origin rule for the team calendar application",
      "action": "route",
      "action_parameters": {
        "origin": {
          "port": 9000
        }
      }
    }
  ]
}'
```

The response contains the complete definition of the ruleset you updated.

```json
---
header: Response
---
{
  "result": {
    "id": "<RULESET_ID>",
    "name": "Origin Rules ruleset",
    "description": "Zone-level ruleset that will execute origin rules.",
    "kind": "zone",
    "version": "2",
    "rules": [
      {
        "id": "<RULE_ID>",
        "version": "1",
        "action": "route",
        "action_parameters": {
          "origin": {
            "port": 9000
          }
        },
        "expression": "starts_with(http.request.uri.path, \"/team/calendar/\")",
        "description": "Origin rule for the team calendar application",
        "last_updated": "2022-06-03T14:42:04.219025Z",
        "ref": "<RULE_REF>"
      }
    ],
    "last_updated": "2022-06-03T14:42:04.219025Z",
    "phase": "http_request_origin"
  },
  "success": true,
  "errors": [],
  "messages": []
}
```

{{</details>}}

---

## Required API token permissions

The API token used in API requests to manage origin rules must have at least the following permission:

* _Origin_ > _Edit_
