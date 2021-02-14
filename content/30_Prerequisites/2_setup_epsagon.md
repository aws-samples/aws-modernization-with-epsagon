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

## Signup and details

Go ahead to Epsagon, sign up and fill in your details:

{{% notice warning %}}
If you've used Epsagon in the past, please make sure to sign up with a NEW account.
{{% /notice %}}

![Signup](/images/prerequisites/signup.png)

![Details](/images/prerequisites/details.png)

## Integrating your AWS account

The integration is straightforward, select the AWS integration, and click on "Integrate AWS":

![CloudFormation](/images/prerequisites/cf.png)

Clicking the button will open a wizard on AWS. Select the box and click create stack:

![CloudFormation](/images/prerequisites/cf_aws.png)

After a minute, the stack creation should be completed, you can head back to Epsagon and see the step is completed:

![CloudFormation](/images/prerequisites/cf_complete.png)

If you need more details on this step, you can read more in the [documentation](https://docs.epsagon.com/docs/getting-started-aws).

## Monitoring your Lambda functions

Epsagon provides an automated tracing library that allows you to gain visibility to every operation and call. You can use the auto-tracing method through Epsagon to quickly enable it for your functions:

![Trace](/images/prerequisites/trace.png)

Or if it is already open, select the four functions that starts with `catalog-shop`, and click auto-trace:

![Trace](/images/prerequisites/tracing.png)

To complete the wizard, let refresh our retail store page a few more time (it will generate traces, which will help us to complete the wizard):

![Complete](/images/prerequisites/complete.png)

Click on view trace button to get into the dashboard.
