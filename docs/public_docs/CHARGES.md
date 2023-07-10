[ Overview](./README.md)

![plot](./images/linkedin.png)

### In development
nb: The FeeWise charges feature is in development, the details below may change

# Charges
A charge is a generic FeeWise artifact that allows a PMS to bill a firm's client for services provided.

# Create a charge - Existing FeeWise Customer
Firms will be able to create a charge for an existing FeeWise customer. (A customer that has already made a charge payment , via FeeWise)

The process for creating a charge for an existing customer is as follows:
* The FeeWise API is used to retrieve the Firm's customers and their stored payment method. (as a tokenised value)
* The PMS user selects a customer and the payment method to use. (token)
* PMS Uses the selected customer's payment method token,  .

# Create a charge - New Customer
If the customer is new to FeeWise, the process is as follows:

* The PMS uses the hosted fields app to collect the customer's payment details.
* The PMS allows the firm to denote that the customer's payment method should be stored for future use.
* The firm's customer makes the payment, FeeWise will store the payment method and return a token to the PMS, in a subsequent webhook (as the customer payment will happen later)

Creating a charge will result in a URL being provided that denotes the location of the FeeWise hosted fields app, to be used for payment.
The PMS hosts the FeeWise hosted fields app in an iframe, and the customer makes the payment.

Once a payment has been created, the Charge may be requested to get the details including its status.

Additionally (and optionally), webhook(s) may be registered to receive events on the progress of the charge.

a charge contains an `external_id`. This is an ID supplied by the PMS/Channel-partner. It must be unique for the
channel-partner and firm_id. This means that a channel partner needs to keep the external_id unique for the firm the
charge is created for. Charges may be [retrieved using this ID](../../reference/partner-openapispec.yaml/paths/~1api~1v3~1partner~1charges~1firm~1{firm_id}~1{external_id}/get)
instead of the FeeWise generated ID

