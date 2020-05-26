+++
title = "Setting up Epsagon"
chapter = false
weight = 2
+++

## Creating an Epsagon account

In order to troubleshoot our recent error with the retail store, let's create and setup an Epsagon account first.

To create an account, head to [Epsagon](https://dashboard.epsagon.com/signup?ref=aws-workshop), and sign up.

{{% notice note %}}
Epsagon provides a completely free trial that fits this workshop needs, and much more!
{{% /notice %}}

If you need any help with or throughout the setup, you can use the [documentation](https://docs.epsagon.com/docs/getting-started-setup).

![Signup](/images/prerequisites/docs.png)

Once you signup, you can fill your personal details.

## Integrating your AWS account

The integration is straightforward, select the AWS integration, and click on "Deploy CloudFormation Stack":

![CloudFormation](/images/prerequisites/cf.png)

If you need more details on this step, you can read more in the [documentation](https://docs.epsagon.com/docs/getting-started-aws).

## Monitoring your Lambda functions

Epsagon provides an automated tracing library that allows you to gain visibility to every operation and call. You can use the auto-tracing method through Epsagon to quickly enable it for your functions:

![Trace](/images/prerequisites/trace.png)

And select the retail store functions.