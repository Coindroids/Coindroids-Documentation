---
title: Events
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Interacting with the Event object through the REST API"

---


## Request

```HTTP
GET https://api.coindroids.com/event
```

## Response Details

|Name|Data Type|Description|
|---|---|---|
|block_hash|String||
|txid|String||
|tx_vout|Whole Number||
|action_type| Action Type | _see data type for options_ |
|value| Whole Number| |
|outcomes| Compact Outcomes[] | An array containing all the related outcomes that occured as result of the action. ||

## Example

### Request

```HTTP
GET /event?txid=eq.3c60def1da16173c7e5377aa32eb0295f006f1153f0973da6dc7ac8c7e421272 HTTP/1.1
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
Content-Location: /event?txid=eq.3c60def1da16173c7e5377aa32eb0295f006f1153f0973da6dc7ac8c7e421272
```

### Response Body
```JSON
[
  {
    "block_hash": "000000000046a0085bd4aaa77ec7a6da407504d42a981f617f62fba25ce1d2d7",
    "txid": "3c60def1da16173c7e5377aa32eb0295f006f1153f0973da6dc7ac8c7e421272",
    "tx_vout": 0,
    "action_type": "Registration",
    "value": 1000000,
    "outcomes": [
      {
        "outcome_id": 1,
        "player_id": 1,
        "droid_id": 2,
        "outcome_type": "Droid registered",
        "value_from": null,
        "value_to": 928,
        "is_orphaned": null
      },
      {
        "outcome_id": 2,
        "player_id": 1,
        "droid_id": 2,
        "outcome_type": "Payout address change",
        "value_from": null,
        "value_to": 928,
        "is_orphaned": null
      },
      {
        "outcome_id": 3,
        "player_id": 1,
        "droid_id": 2,
        "outcome_type": "Refund of overpayment",
        "value_from": null,
        "value_to": 999999,
        "is_orphaned": null
      }
    ]
  }
]
```
