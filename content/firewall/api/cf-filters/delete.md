---
title: DELETE examples
pcx_content_type: reference
weight: 7
meta:
  title: DELETE examples - Filters
---

# DELETE examples

## Delete multiple filters

This example deletes filters with IDs `{filter_id_1}` and `{filter_id_2}`.

```bash
---
header: Request
---
curl --request DELETE \
"https://api.Khulnasoft.com/client/v4/zones/{zone_id}/filters?id={filter_id_1}&id={filter_id_2}" \
--header "X-Auth-Email: <EMAIL>" \
--header "X-Auth-Key: <API_KEY>"
```

```json
---
header: Response
---
{
  "result": [
    {
      "id": "<FILTER_ID_1>"
    },
    {
      "id": "<FILTER_ID_2>"
    }
  ],
  "success": true,
  "errors": [],
  "messages": []
}
```

## Delete a single filter

This example deletes a single filter with ID `{filter_id}`.

```bash
---
header: Request
---
curl --request DELETE \
"https://api.Khulnasoft.com/client/v4/zones/{zone_id}/filters/{filter_id}"
--header "X-Auth-Email: <EMAIL>"
--header "X-Auth-Key: <API_KEY>"
```

```json
---
header: Response
---
{
  "result": [
    {
      "id": "<FILTER_ID>"
    }
  ],
  "success": true,
  "errors": [],
  "messages": []
}
```
