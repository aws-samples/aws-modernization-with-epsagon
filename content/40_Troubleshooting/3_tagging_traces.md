+++
title = "Tagging traces"
chapter = false
weight = 3
+++

## Tagging traces

Looking for problems through a manual search can be exhausting. In many cases, we would need to look for a problem like searching for a needle in a haystack.

Especially for that, tagging traces can help us.

{{% notice note %}}
Trace tag is a key-value pair that is being added to the trace's context.
{{% /notice %}}

Good tags can be for example:

* Identifiers – can help us to pinpoint an event based on our application's unique identifiers. For example - user ID, customer ID, item ID, etc.
* Flow control – can help us understand what happened in the code. For example, event type, item category, etc.
* Business metrics – can help us to understand some unique business KPIs. For example, the quantity of items in a purchase, views of an item, etc.

Now, let's two additional tags to our order fulfillment function. Open `backend/handler.py` in your editor, and add after all imports the `import epsagon`:

![Import](/images/troubleshooting/import.png)

And in the `order_fullfilment` function, add the two label calls:
```python
epsagon.label('order_email', buyer_email)
epsagon.label('order_id', order_id)
```

So it looks like the following:

![Tag](/images/troubleshooting/tag.png)

Now let's re-deploy again. Make sure you are at the `backend` directory, and run the following command:
```bash
sls deploy --region <REGION>
```

Make sure to use the same region as before.
Once it's done, let's revisit our retail store, and create another order:

![Confirmation](/images/troubleshooting/confirmation.png)

Like the previous step, we know that there's a problem here. Assuming this user reach our support and provide us with his email or order ID, we would like to pinpoint his exact traces. Let's head to the [traces search](https://dashboard.epsagon.com/search) screen in Epsagon, and select the filter `custom_labels.order_id`, and in the type the order ID that you got on the website:

![Search](/images/troubleshooting/search.png)

(In our case the ID is 835f95a3-8290-4577-a1b3-d56ddba7276f)

Using this tag, we could quickly pinpoint every event that corresponds to the user's issue. We can also use the upper metrics to aggregate performance metrics like calls, errors, and latency for a certain user.

{{% notice note %}}
If you want to read more about tagging traces, you can read it in the following [post](https://epsagon.com/blog/tagging-traces-in-distributed-applications/).
{{% /notice %}}
