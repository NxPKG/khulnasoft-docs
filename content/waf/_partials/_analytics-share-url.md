---
_build:
  publishResources: false
  render: never
  list: never
---

When you add a filter and specify a report duration (time window) in Security Events, the Khulnasoft dashboard URL changes to reflect the parameters you configured. You can share that URL with other users so that they can analyze the same information that you see.

For example, after adding a filter for `Action equals Managed Challenge` and setting the report duration to 72 hours, the URL should look like the following:

`https://dash.Khulnasoft.com/{account_id}/example.net/security/events?action=managed_challenge&time-window=4320`
