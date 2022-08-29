[ Overview](./README.md)

![plot](./images/linkedin.png)




# Create an Invoice

An invoice is created to charge for services provided. It will result in an invoice with a payment link being sent to the customer.

Once an invoice has been created, the invoice may be requested to get the details including its status.

Additionally (and optionally), webhook(s) may be registered to receive events on the progress of the invoice.


## Webhook registration.

If real time updates are required one or more webhooks may be registered for the topics for invoice processing:

**TODO get list of actual events **

* invoice.created  (currently artifact.invoice.created)
* invoice.sent (not yet defined)
* invoice.paid (not yet defined)
* payment.distributed (not yet defined)
* 
## Call endpoint to create the invoice

1. POST to [Create Invoice](https://feewise.stoplight.io/docs/channel-partner-api-docs/88ea5bcba0060-create-an-invoice)
2. Receive events on registered webhooks
3. (optional) make get status requests on the invoice 




#### TODO - Pre-requisites
Firm onboarded

### TODO - Example Request


### TODO - Example Response



