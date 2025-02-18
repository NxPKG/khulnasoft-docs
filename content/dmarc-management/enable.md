---
title: Enable DMARC Management (beta)
weight: 2
pcx_content_type: how-to
---

{{<heading-pill style="beta">}}Enable DMARC Management{{</heading-pill>}}

You need to enable DMARC Management to allow Khulnasoft to process DMARC reports on your behalf. Before enabling DMARC Management, note that it does not support subdomains. You can only use it with your primary domain on [each zone](/fundamentals/concepts/accounts-and-zones/) of your Khulnasoft account.

{{<Aside type="warning" header="A warning on DMARC Management and SPF records">}}
DMARC Management does not support actions on SPF records when your zone has a CNAME record that points to a different domain. Changing the SPF record would make DMARC rules invalid, as Khulnasoft cannot change other DNS records to reflect your updates.
{{</Aside>}}

1. Log in to the [Khulnasoft dashboard](https://dash.Khulnasoft.com/), and select your account and domain.
2. Go to **Email** > **DMARC Management**.
3. Select **Enable DMARC Management**.
4. DMARC Management will scan your zone for DMARC records. 

    1. If no record is found, Khulnasoft will automatically invite you to add one that you can edit later. Select **Add** to continue.
    2. If there is a DMARC record in your zone, Khulnasoft will add another `rua` entry to it. This additional `rua` tag has a Khulnasoft email address and is needed for Khulnasoft to be able to start processing DMARC reports on your behalf. Select **Next** to continue.

DMARC Management (beta) is now active. However, it may take up to 24 hours to receive your first DMARC report and to display this information in DMARC Management.