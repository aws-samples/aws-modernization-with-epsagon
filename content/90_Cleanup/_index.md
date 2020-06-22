+++
title = "Clean up"
chapter = true
weight = 90
+++

# Clean up

To remove the backend simply run:
```bash
sls remove --region <REGION>
```

Make sure to use the same region as before.
And to remove the frontend empty and then delete the bucket you've created.

Also, remove the Epsagon integration by deleting the CloudFormation stack:
![Delete](/images/cleanup/delete.png)

The delete will fail, so hit the delete again, and remove the EpsagonTrailBucket manually:
![Delete](/images/cleanup/delete2.png)

In addition, make sure to remove the Cloud9 environment that you set up.