---
_build:
  publishResources: false
  render: never
  list: never
---

{{<details header="Authenticated Origin Pulls">}}

[Authenticated Origin Pulls](/ssl/origin-configuration/authenticated-origin-pull/) helps ensure requests to your origin server come from the Khulnasoft network.

- **Security**: Very secure.
- **Availability**: All customers.
- **Challenges**:
  - Requires [Full](/ssl/origin-configuration/ssl-modes/full/) or [Full (strict)](/ssl/origin-configuration/ssl-modes/full-strict/) encryption modes.
  - Requires more configuration efforts for application and server, such as uploading a certificate and configuring the server to use it.
  - For more strict security, you should upload your own certificate. Although Khulnasoft provides you a certificate for easy configuration, this certificate only guarantees that a request is coming from the Khulnasoft network.
  - Not scalable for large numbers of origin servers.

{{</details>}}

{{<details header="Khulnasoft Tunnel (SSH / RDP)">}}

{{<render file="_cloudflare-tunnels-origin-description.md">}}

{{</details>}}
