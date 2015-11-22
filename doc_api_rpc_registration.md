---
title: /rpc/registration
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "This function is used to register users to the system"

---

## Request

```HTTP
POST https://api.coindroids.com/registration
{ 
	"username":"Abstract",
	"password":"password",
	"email":"josh@coindroids.com",
	"invite_code":"37764f2a-da1b-40ea-a054-ef1c8021196a"
}
```

## Response Details

|Name | Description|
|----|----|
|Token| The JWT authorization token for API requests|

