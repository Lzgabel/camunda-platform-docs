---
id: manage-alerts
title: Manage alerts
description: "Camunda Platform 8 can notify you when process instances stop with an error."
---

Camunda Platform 8 can notify you when process instances stop with an error.

There are two forms of notification:

- By email to the email address of your user account
- By webhook

### Create an alert

To create a new alert, take the following steps:

1. Select the **Alert** tab.

![cluster-details](./img/cluster-detail-alerts.png)

2. Click **Create** to create a new alert.

![create-alert](./img/cluster-detail-create-alert.png)

3. Choose between **Email** and **Webhook**.

4. If you select **Email**, click **Create**. No further information is needed. For **Webhook**, complete the additional steps below.

5. To create a **webhook** alert, provide a valid webhook URL that accepts `POST` requests.

![create-alert-webhook](./img/cluster-detail-alerts-webhook.png)

6. You will have one email alert per cluster, but you can create multiple webhook alerts if needed.

### Webhook alerts

Webhook alerts contain a JSON body with following structure:

```json
{
    "clusterName": "cluster-name",
    "clusterId": "88d32bfc-4f8e-4dd3-9ae2-adfee281e223",
    "operateBaseUrl": "https://console.cloud.camunda.io/org/2b3bc239-ad5b-4eef-80e0-6ef5139ed66a/cluster/88d32bfc-4f8e-4dd3-9ae2-adfee281e223/operate",
    "clusterUrl": "https://console.cloud.camunda.io/org/2b3bc239-ad5b-4eef-80e0-6ef5139ed66a/cluster/88d32bfc-4f8e-4dd3-9ae2-adfee281e223",
    "alerts": [
        {
            "operateUrl": "https://console.cloud.camunda.io/org/2b3bc239-ad5b-4eef-80e0-6ef5139ed66a/cluster/88d32bfc-4f8e-4dd3-9ae2-adfee281e223/operate/#/instances/2251799829404548",
            "processInstanceId": "1234567890123456",
            "errorMessage": "something went wrong",
            "errorType": "JOB_NO_RETRIES",
            "flowNodeId": "node-id",
            "jobKey": 1234567890123456,
            "creationTime": "2021-07-22T08:00:00.000+0000",
            "processName": "process-name",
            "processVersion": 1
        }
    ]
}
```
