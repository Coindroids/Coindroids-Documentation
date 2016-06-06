
# API Authentication


```shell
POST /rpc/identify
{
	"username":"Somebody",
	"password":"password"
}
```

```
{"token":"eyJhbGc...adsf5"}
```

```shell
POST /rpc/identify
Authorization: Bearer eyJhbGc...adsf5
```
	

```
{"token":"eyJhbGc...adsf5"}
```


Although anonymous access to the API is permitted, an authorized account will have additional functionality available to them. This section explains initial account creation along with management of the API authorization tokens required to make authenticated requests. 



### Authorization

Authentication is tracked using a JWT formatted authorization token. 

#### Initiating a Session
To initial a session using your login and password, pass the paramters within the body of the request. 




#### Renewing a Session	
Authorization tokens expire every 24 hours but can be updated at any time. To retrieve a new token, simply call the identify function with an authorized request (rather than the username and password). 

<aside class="notice">
Old tokens stay in use until the 24 hour time expires fully
</aside>

