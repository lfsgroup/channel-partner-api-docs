[ Overview](./README.md)

![plot](./images/linkedin.png)


# Create an Invoice

An invoice is created to charge for services provided. Creating an invoice will result in a URL being available that should be sent to the customer. 
The customer follows the link to pay the invoice.

Once an invoice has been created, the invoice may be requested to get the details including its status.

Additionally (and optionally), webhook(s) may be registered to receive events on the progress of the invoice.


## Call endpoint to create the invoice


1. POST to [Create Invoice](../../reference/partner-openapispec.yaml/paths/~1api~1v3~1partner~1invoices/post).  
Note the [Invoice](../../reference/partner-openapispec.yaml/components/schemas/Invoice) returned from the post contains the payment URL needed to pay the invoice.
2. Send the payment URL to the client.
3. Receive events on registered webhooks. (optional)
4. Make GET requests on the invoice to get the payment URL again. (optional)


## Status state changes

| Status        | Meaning                                      |
|---------------|----------------------------------------------|
| Submitted     | The invoice has been accepted by the system. |
| Draft         | Currently unused                             |
| Authorised    | Currently unused                             |
| Voided        | Currently unused                             |


## Webhooks.

If real time updates are required, one or more webhooks must be registered for the topics for invoice processing. Note that 
a URL may be registered for each webhook or for many webhooks.

* invoice.created 
* invoice.updated


### invoice.created
Once the invoice has been created in the system, an event is POSTed to the URL registered for `invoice.created`.
The body is the [event envelop](../../reference/partner-openapispec.yaml/components/schemas/WebhookEvent) containing the created Invoice as the event payload.


### invoice.created
Any change to the invoice after creation will result in an event being POSTed to the URL registered for `invoice.updated`.
The body is the [event envelop](../../reference/partner-openapispec.yaml/components/schemas/WebhookEvent) containing the created Invoice as the event payload.


