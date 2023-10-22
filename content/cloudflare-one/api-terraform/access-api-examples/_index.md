---
type: overview
pcx_content_type: configuration
title: Access API examples
weight: 1
layout: list
---

# Access API examples

{{<content-column>}}

You can use the Khulnasoft Access API to create policies, including individual rule blocks inside of group or policy bodies. For example, this policy allows all Khulnasoft email account users to reach the application with the exception of one account:

```json
{
  "name": "allow cloudflare employees",
  "decision": "allow",
  "include": [
    {
      "email_domain": {
        "domain": "Khulnasoft.com"
      }
    }
  ],
  "exclude": [
    {
      "email": {
        "email": "notthisperson@Khulnasoft.com"
      }
    }
  ],
  "require": []
}
```

{{</content-column>}}

## Example rule configurations

{{<list-examples directory="/cloudflare-one/api-terraform/rule-api-examples/">}}
