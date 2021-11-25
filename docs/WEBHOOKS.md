### Invoice Payment Webhooks
Allow posting of events, such as payments or invoice updates to a predefined webhook.

---

### TODO
...

---

### Webhook authentication
Webhooks support two types of authentication: 

* basic 
* bearer token. 

Both types of authentication should only be used over HTTPS (TLS).

Although not recommended, it's also possible to create a webhook without authentication. To do this, omit the authentication property from the request.

---

### Verifying webhook authenticity
Webhooks provide an additional security measure to verify that the webhook is genuine and has come from RapidPay. This can be useful if you're looking to ensure only RapidPay webhooks are being made to your endpoint and ensure the information is genuine and as the system expects. These signatures will also help prevent against replay attacks. Verifying the signing secret is optional.

Webhook requests will contain two headers which can be used to verify the request's authenticity:

* `X-RapidPay-Webhook-Signature` - the main signature
* `X-RapidPay-Webhook-Signature-Timestamp` - the timestamp used to verify the signature

This is used in conjunction with the payload of the request (if there is one).

TODO - https://developer.zendesk.com/documentation/event-connectors/webhooks/verifying/

#### Verifying the signature
Sign the body and signature timestamp with the webhook secret key using SHA256, then base64 encoding the resulting digest.

Represented simply: base64(HMACSHA256(TIMESTAMP + BODY))

To verify the signature, create the same SHA256 HMAC signature and then compare it to the webhook payload to ensure that they match. If they match, then you can be sure that the webhook came from RapidPay. If they don't, it may be a request from another source.

Not all requests from webhooks will have a body (GETs, DELETEs), so ensure that this scenario is accounted for in any verification code. Depending on language, this may be an empty string or null. Consult your language's documentation for details.

---

### References
https://quickapay.gitbook.io/quickapay-api/webhooks/invoice-payments
https://developer.zendesk.com/documentation/event-connectors/webhooks/webhook-security-and-authentication/
