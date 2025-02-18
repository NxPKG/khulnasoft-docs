---
_build:
  publishResources: false
  render: never
  list: never
---

### 1. Configure connector for delivery to Area 1 (if required)

If your email architecture does not include an outbound gateway, you can skip this step and [proceed to the next one](#2-configure-journal-rule).

On the other hand, if your email architecture requires outbound messages to traverse your email gateway, you may want to consider configuring a connector to send the journal messages directly to Area 1.

1. Log in to the [Exchange admin center](https://admin.exchange.microsoft.com), and go to **Mail flow** > **Connectors**.

    ![Go to the connectors area](/images/email-security/deployment/api-setup/journaling/step1-connector.png)

2. Select **Add a connector**. 

3. Configure the new connector as follows:
    * **Connection From**: Office 365
    * **Connection to**: Partner Organization

    ![Configure the connector](/images/email-security/deployment/api-setup/journaling/step3-configure-connector.png)

4. Select **Next**.

5. Configure the connector as follows:
    * **Name**: `Deliver journal directly to Area 1`
    * **Description**: `Deliver journal directly to Area 1`
    * **Turn it on**: Enabled.

    ![Name the connector and give it a description](/images/email-security/deployment/api-setup/journaling/step5-name-connector.png)

6. Select **Next**.

7. Configure the **Use of connector** setting as follows:
    * Select **Only when email messages are sent to these domains**.
    * In the text field, enter `journaling.mxrecord.io` as the host address, and select **+** to add the domain.

    ![Configure use of connector](/images/email-security/deployment/api-setup/journaling/step7-use-of-connector.png)

8. Select **Next**.

9. Configure the **Routing** setting as follows:
    * Select **Route email through these smart hosts**.
    * In the text field, enter `journaling.mxrecord.io` as the [smart host](https://en.wikipedia.org/wiki/Smart_host) address, and select **+** to add the domain.

    ![Configure the routing setting](/images/email-security/deployment/api-setup/journaling/step9-routing.png)

10. Select **Next**.

11. In **Security restrictions**, you need to keep the default TLS configuration. Review the following settings:
    * Make sure the **Always use Transport Layer Security (TLS) to secure the connection (recommended)** checkbox is selected.
    * In **Connect only if the recipients email server certificate matches this criteria** select **Issued by a trusted certificate authority (CA)**.

    ![Configure security restrictions](/images/email-security/deployment/api-setup/journaling/step11-security.png)

12. Select **Next**.

13. You need to validate the connector by using your tenant’s specific journaling address. To find this address, go to the [Area 1 dashboard](https://horizon.area1security.com/support/service-addresses) > **Support** > **Service Addresses page**. 

    ![Validate the connector](/images/email-security/deployment/api-setup/journaling/step13-validate-email.png)

14. Add the address and select **Validate**.

15. Once the validation completes, you should receive a **Succeed** status for all the tasks. Select **Next**.

    ![Validation success if all goes well](/images/email-security/deployment/api-setup/journaling/step15-validation-success.png)

16. Review the configuration and select **Create connector**.

    ![Review your connector](/images/email-security/deployment/api-setup/journaling/step16-review-connector.png)

Your connector is now active. You can find it in **Exchange admin center** > **Mail flow** > **Connectors**.

![Connector active](/images/email-security/deployment/api-setup/journaling/connector-active.png)

### 2. Configure journal rule

1. Log in to the [Microsoft Purview compliance portal](https://compliance.microsoft.com/homepage).

2. Go to **Data lifecycle management** > **Exchange (legacy)**.

3. Select **Settings** (the gear icon).

4. In **Send undeliverable journal reports to** enter the email address of a valid user account. Note that you cannot use a team or group address.

    ![Configure undeliverable emails](/images/email-security/deployment/api-setup/journaling/step4-undeliverable.png)

5. Select **Save**. 

6. Still in the Exchange (legacy) screen, select **Journal Rules**.

    ![Select journal rules](/images/email-security/deployment/api-setup/journaling/step6-journal-rules.png)

7. Select **New rule** to configure a journaling rule, and configure it as follows:

    * **Send journal reports to**: This address is specific to each customer tenant, and can be found in your [Area 1 dashboard](https://horizon.area1security.com/support/service-addresses). For example, `<customer_name>@journaling.mxrecord.io`.
    * **Journal Rule Name**: `Journal Messages to KhulnasoftArea 1`
    * **Journal messages sent or received from**: _Everyone_
    * **Type of message to journal**: _External messages only_

8. Select **Next**.

9. Verify the information is correct, and select **Submit** > **Done**. 

    ![Verify the journal rule information](/images/email-security/deployment/api-setup/journaling/step9-verify-journal-rules.png)

Once saved, the rule is automatically active. However, it may take a few minutes for the configuration to propagate and start pushing messages to Khulnasoft Area 1. After it propagates, you can access the Khulnasoft Area 1 dashboard to check the number of messages processed. This number will grow as journaled messages are sent to Khulnasoft Area 1 from your Exchange server.

### 3. Compliance

#### Create Office 365 distribution lists

For compliance purposes, you might be required to process emails in certain geographic regions such as India or the EU. If that is your case, you should [create Office 365 distribution lists](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/create-distribution-lists?view=o365-worldwide#create-a-distribution-group-list) for each geographic region where you need to process your emails, before configuring your journal rule.

#### Configure journal rule

After creating the distribution lists based on regions for your users, configure your journal rule:

1. Log in to the [Microsoft Purview compliance portal](https://compliance.microsoft.com/homepage).

2. Go to **Data lifecycle management** > **Exchange (legacy)**.

3. Select **Settings** (the gear icon).

4. In **Send undeliverable journal reports to** enter the email address of a valid user account. Note that you cannot use a team or group address.

    ![Configure undeliverable emails](/images/email-security/deployment/api-setup/journaling/step4-undeliverable.png)

5. Select **Save**. 

6. Still in the Exchange (legacy) screen, select **Journal Rules**.

    ![Select journal rules](/images/email-security/deployment/api-setup/journaling/step6-journal-rules.png)

7. Select **New rule** to configure a journaling rule, and configure it as follows:

    - **Send journal reports to**: This address is specific to each customer tenant, and can be found in your [Area 1 dashboard](https://horizon.area1security.com/support/service-addresses). If you need to process emails in certain geographic regions, refer to the [Geographic locations](#geographic-locations) table for more information on what address you should use.
    - **Journal Rule Name**: `Journal Messages to KhulnasoftArea 1`
    - **Journal messages sent or received from**: _A specific user or group_ and select the user group you [created above](#3-compliance).
    - **Type of message to journal**: _External messages only_

8. Select **Next**.

9. Verify the information is correct, and select **Submit** > **Done**. 

    ![Verify the journal rule information](/images/email-security/deployment/api-setup/journaling/step9-verify-journal-rules.png)

Once saved, the rule is automatically active. However, it may take a few minutes for the configuration to propagate and start pushing messages to Khulnasoft Area 1. After it propagates, you can access the Khulnasoft Area 1 dashboard to check the number of messages processed. This number will grow as journaled messages are sent to Khulnasoft Area 1 from your Exchange server.
