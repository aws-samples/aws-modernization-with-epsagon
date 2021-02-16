+++
title = "Distributed tracing"
chapter = false
weight = 2
+++

## Distributed tracing

Now that our retail store is up and running, let's order something. To do that, simply get into any item, add it to cart check out, and fill some details. For this purpose - let's fill in your real email, because you're about to get a confirmation for your order.

{{% notice note %}}
For a credit card, you can use 4242 4242 4242 4242 with any date and CVC.
{{% /notice %}}

{{% notice note %}}
Make sure to use your REAL email - because we are expected to get an update!
{{% /notice %}}


![Order](/images/troubleshooting/order.png)

You are now a pleased owner of a new item, and you also got a confirmation ID, but no email has arrived. It seems like we are going to troubleshoot our problem again.

Let head back to the functions screen, and now we can see that under `catalog-shop-dev-order-fullfilment` we have a problem:

![Functions](/images/troubleshooting/functions_2.png)

Let's get into this function, but this time, and because this is a distributed and asynchronous flow, let's see an end-to-end trace by clicking on the recent exception invocation ID:


![Functions](/images/troubleshooting/function_2.png)

Which will open the trace window:

![Trace](/images/troubleshooting/trace.png)

A quick examination shows us a full flow from end-to-end, starting at the API Gateway, through an SNS to the second Lambda. We can detect several issues in this trace by clicking on the error nodes:

1. Our client did receive a success confirmation page, although there was an error, and he never got notified of that.
2. Our functions failed, because it couldn't send the email due to `Email address is not verified. The following identities failed the check in region`.
3. Since the function has failed, we had 3 retry attempts. This is a built-in behavior on asynchronous trigger events. If this is being mishandled, it can create inconsistencies in our application.
4. Due to the retry, we updated our stock 3 times, instead of just one, which results in `An error occurred (ConditionalCheckFailedException) when calling the UpdateItem operation` error to our DynamoDB call.

{{% notice note %}}
Our main lesson here is that tracing becomes very crucial in distributed and event-driven architecture. In a few seconds, we mapped out all errors and exceptions, giving us the ability to resolve issues much faster.
{{% /notice %}}

In this workshop, we are not going to cover ways to fix these issues, but as a challenge - you are more than welcome to do so.