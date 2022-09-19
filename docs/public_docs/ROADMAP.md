# API Roadmap

The API and platform is currently under heavy development at this time (September 2022) and is not production ready yet. 
We're targeting a Dec 2022 go-live with production ready APIs at this time.

## Current Status

## Environment
The current available environment is a sandbox environment.
* The platform neither accepts real transactions nor deals with real money
* data is frequently reset - this will mean data such as invoices, webhook registrations etc will be lost. It is recommended to script any setup needed.
* code version changes happen as needed by the development team

Reasonable effort is made to keep this environment stable and working, however, it is not under production support.
Every attempt will be made to notify users of changes, resets etc but that cannot be guaranteed


## API
The API should be considered beta quality. Breaking and non-breaking changes should be expected.
There will be no support for older API versions until version 1.0.x is reached (currently 0.0.x)

## Implementation

## Webhook Management

| Endpoint / Event | Status         |          |
|------------------|----------------|----------|
| List Webhooks    | Implemented    | ✅ |
| Create Webhook   | Implemented    | ✅ |
| Update Webook    | Implemented    | ✅ |
| Delete Webook    | Implemented    | ✅ |


## Invoices

| Endpoint / Event | Status                                                                              |     |
|------------------|-------------------------------------------------------------------------------------|-----|
| Create Invoice   | Partially Implemented (payment URL is valid but the UI is not implemented)          | ✅   |
| Get Invoice      | Implemented. An invoiced created using the Create Invoice endpoint can be retrieved | ✅   |
| invoice.created  | Implemented. Sent on successful call to Create Invoice                              | ✅   |
| invoice.update   | Not Implemented                                                                     | ❌   |       

## Trust Deposits

| Endpoint / Event     | Status                                                                               |          |
|----------------------|--------------------------------------------------------------------------------------|----------|
| Create Trust Deposit | Implemented (check that payment URL is valid)                                        | ✅ |
| Get Trust Deposit    | Implemented. An invoiced created using the Trust Deposit endpoint can be retrieved   | ✅ |
| invoice.created      | Implemented. Sent on successful call to Create Invoice                               | ✅ |
| invoice.update       | Not Implemented                                                                      | ❌ |       

## Payouts

| Endpoint / Event | Status                                                                   |     |
|------------------|--------------------------------------------------------------------------|-----|
| Get Payouts      | Not Implemented - request validation implemented but no results returned | ❌   |
| payout.sent      | Not Implemented                                                          | ❌   | 

## Payments

| Endpoint / Event       | Status                                                                   |     |
|------------------------|--------------------------------------------------------------------------|-----|
| Get Payments           | Not Implemented - request validation implemented but no results returned | ❌   |
| Apply External Payment | Not implemented (allows PMS to record a payment made outside of FeeWise) | ❌   | 
| payment.received       | Not implemented                                                          | ❌   | 

## Token Management
| Endpoint / Event | Status       |    |
|------------------|--------------|----|
| RotateApiKey     | Implemented  |  ✅ |



## Roadmap

### External / partial payments

#### API change 
Add amount_due and payments to an Invoice and TrustDeposit 
Add and update schemas and add path(s) to allow payments made outside FeeWise to be recorded in FeeWise

#### Implementation
Fully implement including HTTP handlers, database updates, and events

### Implement payments

Record payments as they come in and send out events. 
This will activate the payment events and endpoint currently described in the docs

### Implement payouts
Record payouts as they are made and send out events.
This will activate the payout events and endpoint currently described in the docs


