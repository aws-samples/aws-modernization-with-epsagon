+++
title = "Deploying the application"
chapter = false
weight = 1
+++

{{% notice note %}}
Make sure you have [Python](https://www.python.org/), [git](https://git-scm.com/), and [npm](https://www.npmjs.com/get-npm) installed on your host.
{{% /notice %}}

## Deploying the retail store

In this section, we are going to deploy the retail store to your account using two main tools:

1. [The Serverless Framework](https://serverless.com) - for the backend part.
2. [Scotty.js](https://github.com/stojanovic/scottyjs) - for the frontend part.

Let start first with cloning the repository:

```bash
git clone git@github.com:epsagon/retail-store-workshop.git
cd retail-store-workshop
```

### Backend

```bash
cd backend
npm install
npm install -g serverless
sls deploy
```

Upon successful deployment, we can see the following output:

![Endpoint creation](/images/prerequisites/sls_deploy.png)

Make sure to copy the endpoint, because we can use it soon.

Now let's create some items in our stock:
```bash
python update_db.py 4
```

`update_db.py` script puts items (in this case 4) into our DynamoDB.

### Frontend

```bash
cd ../frontend
yarn install
npm install -g scottyjs
```

Now, let's copy the endpoint to the file `frontend/src/config.js`:

![Update config](/images/prerequisites/configjs.png)

Now we can deploy our frontend:
```bash
npm run deploy <BUCKET_NAME>
```

Instead of `<BUCKET_NAME>` choose a unique name for the S3 bucket that will be created for the website. It can be any name! In the example, we are using `observability-workshop-ranrib`.

![Frontend deployed](/images/prerequisites/frontend_deployed.png)

## Getting to the retail store

Now that our store is live, let's open our browser and get to it:

![Retail store](/images/prerequisites/retail_store.png)

{{% notice warning %}}
At this point, you'll probably see a loading circle that never ends... That's a starting point for troubleshooting!
{{% /notice %}}
