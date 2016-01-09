---
title: /rpc/create_droid
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Create a new droid"

---

This RPC call requires an authentication request.

## Request

```HTTP
POST https://api.coindroids.com/create_droid
{ 
	"name":"Droidzilla",
	"currency_id":1,
	"model_id":4
}
```

## Response Details

_Returns a Droid object_


