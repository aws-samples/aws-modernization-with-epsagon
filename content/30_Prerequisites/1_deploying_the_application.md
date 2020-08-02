+++
title = "Deploying the application"
chapter = false
weight = 1
+++

{{% notice note %}}
Make sure you have [Python](https://www.python.org/), [git](https://git-scm.com/), and [npm](https://www.npmjs.com/get-npm) installed on your host. If you're using Cloud9 environment everything is already installed.
{{% /notice %}}

## Deploying the retail store

In this section, we are going to deploy the retail store to your account using two main tools:

1. [The Serverless Framework](https://serverless.com) - for the backend part.
2. [Scotty.js](https://github.com/stojanovic/scottyjs) - for the frontend part.

Let start first with cloning the repository:

```bash
git clone https://github.com/epsagon/retail-store-workshop.git
cd retail-store-workshop
```

### Backend

To deploy run the following commands. Make sure to replace `<REGION>` with your desired region. In our example we are using `eu-west-1`.

```bash
cd backend
npm install
npm install -g serverless
sls deploy --region <REGION>
```

Upon successful deployment, we can see the following output:

![Endpoint creation](/images/prerequisites/sls_deploy.png)

Make sure to copy the endpoint, because we can use it soon.

Now let's create some items in our stock:
```bash
python update_db.py 4 <REGION>
```

`update_db.py` script puts items (in this case 4) into our DynamoDB. Make sure to use the same region as before.

### Frontend

```bash
cd ../frontend
npm install -g yarn scottyjs
yarn install
```

Now, let's copy the endpoint to the file `frontend/src/config.js`:

![Update config](/images/prerequisites/configjs.png)

Make sure to change only to hostname part, and leave the string ending with `/dev`.

Now we can deploy our frontend:
```bash
npm run deploy <BUCKET_NAME>
```

If requested, select the region as the same `<REGION>` you've used before:

![Scotty](/images/prerequisites/scotty_region.png)

{{% notice note %}}
Note: This is a public bucket to host the static website. This name must be unique.
If you encounter an Access Denied error, please note that it is mandatory to have permissions to create a public S3 Bucket.
{{% /notice %}}

Instead of `<BUCKET_NAME>` choose a unique name for the S3 bucket that will be created for the website. It can be any name! In the example, we are using `observability-workshop-ranrib`.

![Frontend deployed](/images/prerequisites/frontend_deployed.png)

## Getting to the retail store

Now that our store is live, let's open our browser and get to it:

![Retail store](/images/prerequisites/retail_store.png)

{{% notice warning %}}
At this point, you'll probably see a loading circle that never ends... That's a starting point for troubleshooting!
{{% /notice %}}
