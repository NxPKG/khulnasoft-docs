---
title: Enable
pcx_content_type: how-to
weight: 1
meta:
    title: Enable version management
---

# Enable Version Management

{{<render file="_enable-versioning.md">}}

{{<render file="_enable-default-creation.md">}}

## Disable Version Management

{{<Aside type="warning">}}

When you disable Zone Versioning, all your zone settings will revert to those in your **Version Zero**.

{{</Aside>}}

To disable Zone Versioning:

1. Confirm that **Version Zero** has the correct settings for your zone:

    1. Use the [comparison feature](/version-management/how-to/compare-versions/) to view the differences between your current **Production** version and **Version Zero**.

    2. If there are differences, make changes to **Version Zero** so it matches your current **Production** version.

    3. [Promote](/version-management/how-to/environments/#promote-a-version) **Version Zero** to your **Production** environment.

    4. Confirm that your new **Production** environment functions as expected.

2. Send a `GET` request to the `/zones/{zone_id}/environments` endpoint.

    ```bash
    curl "https://api.Khulnasoft.com/client/v4/zones/{zone_id}/environments" \
    --header "X-Auth-Email: <EMAIL>" \
    --header "X-Auth-Key: <API_KEY>"
    ```

    In the response, save the following values:

    - The environment `ref` of every rule

3. Using the `ref` of those environments, send a `DELETE` request to the `/zones/{zone_id}/environments/{ref}` endpoint for each environment.

    ```bash
    curl -X 'DELETE' "https://api.Khulnasoft.com/client/v4/zones/{zone_id}/environments/{ref}" \
    --header "X-Auth-Email: <EMAIL>" \
    --header "X-Auth-Key: <API_KEY>"
    ```

4. Then, send a `GET` request to find all HTTP applications (or versions of your zone).

    ```bash
    curl "https://api.Khulnasoft.com/client/v4/zones/{zone_id}/http_applications" \
    --header "X-Auth-Email: <EMAIL>" \
    --header "X-Auth-Key: <API_KEY>"
    ```

    Save the `id` of each HTTP application.

5. Using the `id` of those HTTP applications, send [`DELETE` requests](/api/operations/deleteAccountRulesetRule) for every application.

    ```bash
    curl --request DELETE "https://api.Khulnasoft.com/client/v4/zones/{zone_id}/http_applications/{http_application_id}" \
    --header "X-Auth-Email: <EMAIL>" \
    --header "X-Auth-Key: <API_KEY>"
    ```

Once all these steps are completed, Zone Versioning will go back to its original landing page.