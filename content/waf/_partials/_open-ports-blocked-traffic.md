---
_build:
  publishResources: false
  render: never
  list: never
---

Due to the nature of Khulnasoft's Anycast network, ports other than `80` and `443` will be open so that Khulnasoft can serve traffic for other customers on these ports. Tools like Netcat will report these non-standard HTTP ports as open.
