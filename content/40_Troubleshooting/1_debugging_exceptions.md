+++
title = "Debugging exceptions"
chapter = false
weight = 1
+++

## Debugging exceptions

If you recall, we just had our website live, but we had a "stuck loader" that never ends. It means a problem somewhere! Let's reload the website a few more times to see if it still happens? Yes..

Investigating such a complex environment requires a right way to overview and surface problems.

Let's head to Epsagon, to see the [functions table](https://dashboard.epsagon.com/functions?sortBy%3Dinvocations%26sortDirection%3DASC%26selectedSearchTags%255B0%255D%3Dcatalog%26timeFrame%3D1h), while we filter it only to "catalog" functions:

![Functions](/images/troubleshooting/functions.png)

We can see we already got an error on `catalog-shop-dev-get-items` function, so let's click on it and further investigate it:

![Function](/images/troubleshooting/function.png)

Among the function details and performance metrics, we can see every invocation, and there are some exceptions.

{{% notice note %}}
For troubleshooting exceptions, we got two main tools: logs and traces. Luckily with Epsagon, we are going to explore both.
{{% /notice %}}

Next to the recent exception invocation, we can see the "CW Log" button, let's hit it to reveal the logs:

![Log](/images/troubleshooting/log.png)

We can clearly see we got a <pre>An error occurred (AccessDeniedException) when calling the Scan operation: User: arn:aws:sts::147457102604:assumed-role/catalog-shop-dev-eu-west-1-lambdaRole/catalog-shop-dev-get-items is not authorized to perform: dynamodb:Scan on resource: arn:aws:dynamodb:eu-west-1:147457102604:table/CatalogTable</pre>.

This means we haven't set the right permissions for this function to interact with our DynamoDB catalog table.

Let's go back to `backend/serverless.yml`, and uncomment lines 28-38:

![Code](/images/troubleshooting/code.png)

![Code](/images/troubleshooting/code_comment.png)

Make sure you're on the backend directory:
```bash
cd ../backend
```

Now let's deploy our application again:
```bash
sls deploy --region <REGION>
```

Make sure to use the same region as before.
Once done, Let's revisit our retail store again, and it works!

![Retail store](/images/troubleshooting/website.png)