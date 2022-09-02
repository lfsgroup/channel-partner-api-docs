[ Overview](./README.md)

![plot](./images/linkedin.png)


# Payout Events

As payouts are made by the system, events may be sent to any registered webhooks


## Webhooks Subscription

### payout.sent 

[Register a webhook](../../reference/partner-openapispec.yaml/paths/~1api~1v3~1partner~1webhooks/post) URL to 
receive the webhook event type `payout.sent`

Events posted to that URL for that event type will contain an 
[event envelop](../../reference/partner-openapispec.yaml/components/schemas/WebhookEvent) containing a 
[Payout](../../reference/partner-openapispec.yaml/components/schemas/Payout) 

