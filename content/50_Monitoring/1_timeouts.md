+++
title = "Timeouts"
chapter = false
weight = 1
+++

## Timeouts

Lambda functions bring with them some new limitations that we need to handle as part of the overall monitoring, for example - a limited amount of memory and time, according to our configuration.

Being aware of such issues is crucial, so let's have an example of a timeout issue to understand how it looks like.

To create a timeout on our store, let's increase the number of items in stock from 4 to 17 by running update_db.py script in the backend folder:
```bash
python update_db.py 17
```

Let's revisit our retail store now. We can see that the loader is stuck again, but why?

Let's get back again to to `catalog-shop-dev-get-items` to understand what happened:

![Timeout](/images/monitoring/timeout.png)

To get more details, let's click in the request ID to find out more details in the trace, and switch to the timeline view:

![Timeline](/images/monitoring/timeline.png)

We can easily identify that we are calling an API over and over again, to fetch images for every item in our catalog.
This is not a best practice, especially when our catalog can grow to thousands of items.

Possible solutions for this issue can be:

1. Increasing the timeout duration, from 1 second to more. This can only be a temporary fix, and not the right solution.
2. Offloading the images lookup into a background task that can run periodically in batches of items.
3. Parallelizing the images lookup - can be very costly in network and CPU.
