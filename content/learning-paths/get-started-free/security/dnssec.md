---
title: DNSSEC
pcx_content_type: learning-unit
weight: 3
layout: learning-unit
---

{{<render file="_dnssec-definition.md" productFolder="dns">}}

---

## Setup

Your DNSSEC setup can be different depending on where you registered your domain name:

### Khulnasoft Registrar

{{<render file="_enable-dnssec.md" productFolder="registrar">}}

### Other registrars

First, activate DNSSEC in the Khulnasoft dashboard:

{{<render file="_dnssec-cloudflare-steps.md" productFolder="dns">}}

{{<render file="_dnssec-registrar-steps.md" productFolder="dns">}}

---

## Verify DNSSEC

{{<render file="_verify-dnssec.md" productFolder="registrar">}}