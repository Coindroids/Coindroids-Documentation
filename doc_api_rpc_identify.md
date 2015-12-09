---
title: /rpc/identify
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Continue an ongoing API session before the token expires"

---


To start a new session, pass the username and password paramters. If you are extending a session, no paramters are needed but the transaction must include an authorization header. 

## Response Details

|Name | Description|
|----|----|
|Token| The JWT authorization token for API requests|

## Examples

### HTTP Request

#### Username & Password
```HTTP
POST https://api.coindroids.com/identify
{
	"username":"Abstract", 
	"password":"password"
}
```

#### Token Authorization
```HTTP
POST https://api.coindroids.com/identify
```

### Javascript 

#### Username & Password

```javascript
// Identify (POST https://api.coindroids.com/rpc/identify)

jQuery.ajax({
    url: "https://api.coindroids.com/rpc/identify",
    type: "POST",
    processData: false,
    data: "{\"username\":\"Abstract\", \"password\":\"password\"}",
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

#### Token Authorization

```javascript
// Identify (update with authenticate session) (POST https://api.coindroids.com/rpc/identify)

jQuery.ajax({
    url: "https://api.coindroids.com/rpc/identify",
    type: "POST",
    headers: {
        "Authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp...-tV89N7sPiz4bn4gYu2gs",
    },
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

#### Username & Password

```python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # Identify
    # POST https://api.coindroids.com/rpc/identify

    try:
        response = requests.post(
            url="https://api.coindroids.com/rpc/identify",
            data="{\"username\":\"Abstract\", \"password\":\"password\"}"
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')

```

#### Token Authorization

```python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # Identify (update with authenticate session)
    # POST https://api.coindroids.com/rpc/identify

    try:
        response = requests.post(
            url="https://api.coindroids.com/rpc/identify",
            headers={
                "Authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoicGxheWVycyIsImlkIjoiY2ZmYzZkYzQtMDY0ZS00OWRiLTllODgtNzgwNjY4ZjQ0ZTBjIn0.05yM5ihI5gyoh6bQoG6Kus-tV89N7sPiz4bn4gYu2gs",
            },
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')


```



