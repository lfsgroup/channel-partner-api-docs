[ Overview](./README.md)

![plot](./images/linkedin.png)


# Create a Trust Deposit

A trust deposit is created to request money be paid into a trust. Creating a trust deposit will result in a URL being available that should be sent to the customer. 
The customer follows the link to pay into the trust.

Once an trust deposit has been created, the trust deposit may be requested to get the details including its status.

Additionally (and optionally), webhook(s) may be registered to receive events on the progress of the trust deposit.


## Call endpoint to create the trust deposit


1. POST to [Create Trust Deposit](../../reference/partner-openapispec.yaml/paths/~1api~1v3~1partner~1trust-deposits/post).  
Note the [TrustDeposit](../../reference/partner-openapispec.yaml/components/schemas/TrustDeposit) returned from the post contains the payment URL needed to pay into the trust account.
2. Send the payment URL to the client.
3. Receive events on registered webhooks. (optional)
4. Make GET requests on the invoice to get the payment URL again. (optional)


## Status state changes

| Status        | Meaning                                            |
|---------------|----------------------------------------------------|
| Submitted     | The trust deposit has been accepted by the system. |
| Draft         | Currently unused                                   |
| Authorised    | Currently unused                                   |
| Voided        | Currently unused                                   |


## Webhooks.

If real time updates are required, one or more webhooks must be registered for the topics for invoice processing. Note that 
a URL may be registered for each webhook or for many webhooks.

* trust_deposit.created 
* trust_deposit.updated


### trust_deposit.created
Once the trust deposit has been created in the system, an event is POSTed to the URL registered for `trust_deposit.created`.
The body is the [event envelop](../../reference/partner-openapispec.yaml/components/schemas/WebhookEvent) containing the created [TrustDeposit](../../reference/partner-openapispec.yaml/components/schemas/TrustDeposit) as the event payload.


### trust_deposit.created
Any change to the trust deposit after creation will result in an event being POSTed to the URL registered for `trust_deposit.updated`.
The body is the [event envelop](../../reference/partner-openapispec.yaml/components/schemas/WebhookEvent) containing the created [TrustDeposit](../../reference/partner-openapispec.yaml/components/schemas/TrustDeposit) as the event payload.


