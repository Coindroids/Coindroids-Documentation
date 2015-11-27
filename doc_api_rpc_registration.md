---
title: /rpc/registration
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "This function is used to register users to the system"

---

## Response Details

|Name | Description|
|----|----|
|Token| The JWT authorization token for API requests|

## Examples

### HTTP Request


```HTTP
POST https://api.coindroids.com/registration
{ 
	"username":"Abstract",
	"password":"password",
	"email":"josh@coindroids.com",
	"invite_code":"37764f2a-da1b-40ea-a054-ef1c8021196a"
}
```


### Javascript

```javascript
// Register a player (POST http://104.37.194.182:3000/rpc/register)

jQuery.ajax({
    url: "http://104.37.194.182:3000/rpc/register",
    type: "POST",
    processData: false,
    data: "{ 
	\"username\":\"Abstract\",
	\"password\":\"password\",
	\"email\":\"josh@coindroids.com\",
	\"invite_code\":\"37764f2a-da1b-40ea-a054-ef1c8021196a\"

}",
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

### Python

```python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # Register a player
    # POST http://104.37.194.182:3000/rpc/register

    try:
        response = requests.post(
            url="http://104.37.194.182:3000/rpc/register",
            data="{ 
	\"username\":\"Abstract\",
	\"password\":\"password\",
	\"email\":\"josh@coindroids.com\",
	\"invite_code\":\"37764f2a-da1b-40ea-a054-ef1c8021196a\"

}"
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')

```



