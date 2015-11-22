---
title: Player Profile
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Interacting with the Event object through the REST API"

---

Authorization is required for requests to the /profile endpoint.

## Request

```HTTP
GET https://api.coindroids.com/profile
```

```HTTP
PATCH https://api.coindroids.com/profile
{  
	"password_hash":"somethingelse",
	"email":"my_new_email@addresses.com"
}
```

## Response Details

|Name|Data Type|Description|
|---|---|---|
| username | String | The players username|
| password_hash | String | This value is empty during a select but can be updated |
| email | String | The users email account |



