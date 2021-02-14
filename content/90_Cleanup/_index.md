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

To remove the frontend S3 bucket that was created, let's run:
```bash
cd ../frontend
scotty -d -b <BUCKET_NAME> -r <REGION>
```

Make sure to use the same region and bucket name as before.
And to remove the frontend empty and then delete the bucket you've created.

Also, remove the Epsagon integration by deleting the CloudFormation stack:
![Delete](/images/cleanup/delete.png)

The delete will fail, so hit the delete again, and remove the EpsagonTrailBucket manually:
![Delete](/images/cleanup/delete2.png)

In addition, make sure to remove the following resources:
1. Cloud9 environment that you set up.
2. IAM user that you've created