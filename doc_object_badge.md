---
title: Badges
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Interacting with Badges through the REST API"

---

_Badges are not working yet_

## Request

```HTTP
GET https://api.coindroids.com/badge
```

## Response Details

|Name|Data Type|Description|
|---|---|---|
|id | Whole Number| The badges unique ID |
| name | String| Name of the badge|
|description| String| Short blurb about the badge. |
|npc_id| Whole Number| The ID of the NPC destroyed to attain the badge|
|image| URL | Address to the badge image|

## Example

### Request

```HTTP
GET /badge HTTP/1.1
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
Content-Location: /badge
```

### Response Body
```JSON

```
