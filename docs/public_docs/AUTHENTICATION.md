[Overview](./README.md)

![plot](./images/linkedin.png)

# Authentication
FeeWise APIs may be consumed by Channel Partners 
(and, when requested by the Channel Partner, individual firms).

The main use case is for Channel Partners. 
Some endpoints are available so firms can manage their resources directly.


---

## Authentication - Channel Partners
FeeWise will provide partners with the keys and secrets (api-key and channel partner ID) to use the api.

Requirements for channel partner API authentication are below:

All requests to channel partner endpoints must include an `X-CHANNEL-PARTNER-ID` header, and an `X-API-KEY` header.

### Keys provided to partners

#### X-CHANNEL-PARTNER-ID
The channel partner ID is

* provided during on-boarding.
* a unique identifier for the partner.
* a required header for all requests.


#### X-API-KEY
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

---

## Authentication - Firms
Practice management systems may provide firms with ids and secrets (firm ID and api-key) that will allow a firm to use the api. 
Only endpoints that allow firm scoped security can be used.
Firm requests to firm-scoped endpoints must include the `X-FIRM-ID` and `X-FIRM-API-KEY` headers.

### Keys provided to firms

#### X-FIRM-ID
The firm ID is...

* provided during on-boarding.
* a unique identifier for the firm.
* a required header for all requests authenticated at the firm level.

#### X-FIRM-API-KEY
The X-FIRM-API-KEY key is...

* provided by your practice management system, or by FeeWise, when requested by the Channel Partner.
* required for all requests authenticated at the Firm level.

