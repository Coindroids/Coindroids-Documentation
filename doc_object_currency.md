---
title: Currency
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Interacting with the avialable currencies through the REST API"

---

## Request

```HTTP
GET https://api.coindroids.com/currency
```

## Response Details

|Name|Data Type|Description|
---|---|---|
| id | Whole Number| The ID of the Currency|
| name | String| The science-given name of the Currency |
|token_size| Whole Number | |
|regsitration_fee| Whole Number | The token amout to register a droid under this currency|
|satoshis_per_coin| Whole Number | The amount of satoshis in one coin|



## Example

### Request

```HTTP
GET /currency HTTP/1.1
Host: api.coindroids.com:3000
Connection: close
User-Agent: YourBrowser
```

### Response header

```HTTP
HTTP/1.1 200 OK
transfer-encoding: chunked
Date: Sun, 22 Nov 2015 01:56:37 GMT
Server: postgrest/0.3.0.0
Content-Type: application/json
Content-Range: 0-0/1
Content-Location: /currency
```

### Response Body
```JSON
[
  {
    "id": 1,
    "name": "Bitcoin Testnet",
    "starting_height": 579230,
    "netcode": "XTN",
    "token_size": 10000,
    "registration_fee": 1,
    "satoshis_per_coin": 100000000,
    "last_ingested": null,
    "last_processed": null
  },
  {
    "id": 2,
    "name": "Defcoin Mainnet",
    "starting_height": 332812,
    "netcode": "DFC",
    "token_size": 1000000,
    "registration_fee": 1,
    "satoshis_per_coin": 100000000,
    "last_ingested": null,
    "last_processed": null
  },
  {
    "id": 3,
    "name": "Bitcoin Mainnet",
    "starting_height": 377312,
    "netcode": "BTC",
    "token_size": 10000,
    "registration_fee": 1,
    "satoshis_per_coin": 100000000,
    "last_ingested": null,
    "last_processed": null
  }
]
```
