+++
title = "Configuring alerts"
chapter = false
weight = 3
+++

## Configuring alerts

No monitoring solution is complete without alerting. Alerts give us the confidence to know that our application is running correctly, and when it isn't - to be notified about it.

Let's set our first alert, by getting into the alerts screen, and click "create new alert" button. Fill in the following details:

![Alerts](/images/monitoring/alerts.png)

Make sure to select all 4 functions that start with "catalog-shop-dev-", and use your real email - because we are going to get a real alert!

To get an alert, let's browse our retail store to create some errors (timeouts or exceptions).

{{% notice note %}}
Emails are usually not the best destination for alerts. Epsagon provides built-in integration to tools such as PagerDuty, OpsGenie, Slack, and more.
{{% /notice %}}

After a few minutes, you should see an email in your inbox:

![Email](/images/monitoring/email.png)

You can click on explore, to get more details about the issue.
