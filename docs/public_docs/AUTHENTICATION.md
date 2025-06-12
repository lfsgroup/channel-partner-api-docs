[Overview](./README.md)

![plot](./images/linkedin.png)

# Authentication
Our APIs may be consumed by both Channel Partners (users that run Practice Management Systems) and individual firms.

The main use case is for Channel Partners, but some endpoints are available so firms can manage their resources directly.

<br />
---
<br />

## Authentication - Channel Partners
FeeWise will provide you with the keys and secrets (api-key and channel partner ID) that you will allow the use of our api.

The security schemes required for channel partner API authentication are below:

```yaml json_schema
$ref: "../../reference/partner-openapispec.yaml#/components/securitySchemes/PartnerAuth"
```

```yaml json_schema
$ref: "../../reference/partner-openapispec.yaml#/components/securitySchemes/APIAuth"
```

### Keys provided to partners

### X-CHANNEL-PARTNER-ID
The channel partner ID is

* provided during on-boarding.
* a unique identifier for the partner.
* a required header for all requests.


### X-API-KEY
The X-API-KEY key is...

* provided during on-boarding.
* required for all requests authenticated at the Channel Partner level
* able to be rotated by using the `/rotate-key` endpoint (example for the US region below). Your previous key will continue functioning for the number of hours specified in the request, and you will receive an email when the previous key is retired. You may also refer to the below request, for a general example of making an authenticated request as a channel partner.

```json http
{
  "method": "POST",
  "baseUrl": "https://us.getfeewise.com/api",
  "url": "/v3/partner/rotatekey",
  "headers": {
    "X-CHANNEL-PARTNER-ID": "your-channel-partner-ID",
    "X-API-KEY": "your-current-api-key"
  },
  "body": {
    "previous_key_expires_hours": 24
  }
}
```

<br />
---
<br />

## Authentication - Firms
Practice management systems will provide firms with their keys and secrets (api-key and firm ID) that will allow the use of our api. For unintegrated firms, these keys will be provided by FeeWise directly.

### Keys provided to firms

### X-FIRM-ID
The firm ID is...

* provided during on-boarding.
* a unique identifier for the firm.
* a required header for all requests authenticated at the firm level.

### X-FIRM-API-KEY
The X-FIRM-API-KEY key is...

* provided by your practice management system, or by FeeWise for unintegrated firms.
* required for all requests authenticated at the Firm level.

#### Example request

```json http
{
  "method": "POST",
  "baseUrl": "https://us.getfeewise.com/api",
  "url": "/v3/partner/invoices",
  "headers": {
    "X-FIRM-ID": "your-firm-id",
    "X-FIRM-API-KEY": "your-current-api-key"
  },
  "body": {
    "firm_id": "your-firm-id",
        "external_id": "inv-99",
        "amount": "200",
        "artifact_type": "Invoice",
        "external_reference": "REF-001",
        "settlement_account_type": "Office",
      "matter": {
        "external_id": "matter-99",
        "external_reference": "MY-MATTER",
        "description": "A serious legal matter",
        "type": "A type of matter"
      },
      "debtor": {
        "external_id": "debtor-99",
        "name": "John Doe",
        "email": "john@doe.com",
        "contact_number": "1800 FEE WISE"
      }
  }
}
```
