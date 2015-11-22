---
title: /rpc/identify
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Continue an ongoing API session before the token expires"

---

This RPC call requires an authentication request.

## Request

```HTTP
POST https://api.coindroids.com/identify
```

## Response Details

|Name | Description|
|----|----|
|Token| The JWT authorization token for API requests|


