---
title: Authentication
tags: [API, Authentication, JWT, Authorization, Bearer]
keywords: api, authentication 
last_updated: November 21, 2015
summary: "Authentication to the Coindroids REST API"

---


Although anonymous access to the API is permitted, an unauthorized account will have additional functionality available to them. This section explains initial account creation along with management of the API authorization tokens required to make authenticated requests. 


### Registration

##### REST Request

```HTTP
POST /rpc/register
{ 
	"username":"Somebody",
	"password":"password",
	"email":"somebodys@email.address",
	"invite_code":"uuid-uuid-uuid-uuid-uuid"
}
```

##### Returns

```JSON
{"token":"eyJhbGc...52Zg"}
```	

### Authorization

Authentication is tracked using a JWT formatted authorization token. 

#### Initiating a Session
To initial a session using your login and password, pass the paramters within the body of the request. 

##### REST Request

```HTTP
POST /rpc/identify
{
	"username":"Somebody",
	"password":"password"
}
```
##### Returns

```JSON
{"token":"eyJhbGc...adsf5"}
```

#### Renewing a Session	
Authorization tokens expire every 24 hours but can be updated at any time. To retrieve a new token, simply call the identify function with an authorized request (rather than the username and password). 

##### REST Request

```HTTP
POST /rpc/identify
Authorization: Bearer eyJhbGc...adsf5
```
	
##### Returns

```JSON
{"token":"eyJhbGc...adsf5"}
```

Old tokens stay in use until the 24 hour time expires fully.	

