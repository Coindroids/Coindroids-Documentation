---
title: Player Invite Codes
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Interacting with the Invite Codes through the REST API"

---

## Request

```HTTP
GET https://api.coindroids.com/player_invite
```

## Response Details

|Name|Data Type|Description|
|---|---|---|
| code | UUID | The invitation code to share with your friends|
| invited_id | Whole Number | The ID of the player who uses the invitation code|

## Example

### Request

```HTTP
GET /player_invite HTTP/1.1
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
Content-Location: /player_invite?invited_id=is.null
```

### Response Body
```JSON
[
  {
    "code": "5b0ccaaa-f3b7-48f0-a6c6-75b2b527fb1e",
    "invited_id": null
  },
  {
    "code": "f31cdbcf-0bff-402f-a656-600062e123eb",
    "invited_id": null
  },
  {
    "code": "e8e1cd1e-48d8-4520-8abf-92313fbb1a88",
    "invited_id": null
  }
]
```
