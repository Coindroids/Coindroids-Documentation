---
title: Players
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Interacting with the Players object through the REST API"

---

## Request

```HTTP
GET https://api.coindroids.com/player
```

## Response Details

|Name|Data Type|Description|
|---|---|---|
|id| Whole Number| The players unique identifier|
|username | String | A players unique username|
|droids| Whole Number[]| A list of identifier numbers that represent droids owned by the player|

## Example

### Request

```HTTP
GET /player HTTP/1.1
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
Content-Location: /player
```

### Response Body
```JSON
[
  {
    "id": 2,
    "username": "Abstrcter",
    "droids": [
      3
    ]
  },
  {
    "id": 1,
    "username": "Abstrct",
    "droids": [
      1,
      2
    ]
  }
]
```
