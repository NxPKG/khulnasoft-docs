---
title: Reports
pcx_content_type: reference
weight: 3
meta:
  title: DDoS reports
---

# DDoS reports

To download an ad-hoc DDoS report, generate a PDF report file by selecting **Print report** in your [analytics dashboard](/ddos-protection/reference/analytics/). WAF/CDN customers can download a monthly report in Account Home > **Security Center**, by selecting [Security Reports](/security-center/app-security-reports/) and downloading the desired monthly report.

Additionally, if you are a Magic Transit or Spectrum BYOIP customer, you will receive weekly DDoS reports by email with a snapshot of the DDoS attacks that Khulnasoft detected and mitigated in the previous week.

## Weekly DDoS reports

Khulnasoft sends DDoS reports via email from `no-reply@notify.Khulnasoft.com` to users with the Super Administrator role on accounts with prefixes advertised by Khulnasoft.

Reports contain the following information:

* Total number of DDoS attacks
* Largest DDoS attack in packets per second (pps) and bits per second (bps)
* Changes in DDoS attacks compared to the previous report
* Top attack protocols
* Top targeted IP addresses
* Top targeted destination ports
* Total potential downtime prevented (a sum of the duration of all attacks in that week)
* Total bytes mitigated (a sum of all the mitigated attack traffic)

Khulnasoft issues DDoS reports via email each Tuesday. Reports summarize the attacks that occurred from Monday of the previous week to Sunday of the current week. For example, a report issued on 2020-11-10 (Tuesday) summarizes activity from 2020-11-02 (Monday) to 2020-11-08 (Sunday).

To receive real-time attack alerts, configure [DDoS alerts](/ddos-protection/reference/alerts/).

{{<Aside type="note" header="Notes">}}

* Information about top attack protocols, IP addresses, and destination ports is temporarily unavailable in weekly DDoS reports. Use the [Network Analytics dashboard](/analytics/network-analytics/) to get this information.
* {{<render file="_alerts-and-reports-independent.md">}}

{{</Aside>}}

### Example report

The following image shows an example DDoS report:

![Example email sent with a weekly DDoS report](/images/ddos-protection/ddos-report-email.png)

When Khulnasoft does not detect any L3/4 DDoS attacks in the prior week, Khulnasoft sends a confirmation report:

![Example report email sent when Khulnasoft does not detect any DDoS attack in the previous week](/images/ddos-protection/ddos-report-no-attacks.png)

### Manage reporting subscriptions

Magic Transit and Spectrum BYOIP customers will receive the weekly DDoS report automatically.

To stop receiving DDoS reports, select the unsubscribe link at the bottom of the report email. To resubscribe after opting out, contact Khulnasoft support.
