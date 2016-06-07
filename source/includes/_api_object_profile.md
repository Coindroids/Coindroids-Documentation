 
## /profile 

> View Profile (GET)

```shell 
curl -X "GET" "https://api.coindroids.com/profile" \
	-H "Authorization: Bearer eyJhb...2Y"
```

```javascript
// Viewing current password hash or email (GET https://api.coindroids.com/profile)

jQuery.ajax({
    url: "https://api.coindroids.com/profile",
    type: "GET",
    headers: {
        "Authorization": "Bearer eyJhb...2Y",
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

```python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # Viewing current password hash or email
    # GET https://api.coindroids.com/profile

    try:
        response = requests.get(
            url="https://api.coindroids.com/profile",
            headers={
                "Authorization": "Bearer eyJhb...2Y",
            },
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')


```


> Password Update Example (PATCH)

```javascript
// Updating a password or email (PATCH https://api.coindroids.com/profile)

jQuery.ajax({
    url: "https://api.coindroids.com/profile",
    type: "PATCH",
    headers: {
        "Authorization": "Bearer eyJhb...2Y",
        "Content-Type": "text/plain; charset=utf-8",
    },
    processData: false,
    data: "{ \"password_hash\":\"my new l33t password\" }",
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

```shell
curl -X "PATCH" "https://api.coindroids.com/profile" \
	-H "Authorization: Bearer eyJhb...2Y" \
	-H "Content-Type: text/plain; charset=utf-8" \
	-d "{ \"password_hash\":\"my new l33t password\" }"

```

```python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # Updating a password or email
    # PATCH https://api.coindroids.com/profile

    try:
        response = requests.patch(
            url="https://api.coindroids.com/profile",
            headers={
                "Authorization": "Bearer eyJhb...2Y",
                "Content-Type": "text/plain; charset=utf-8",
            },
            data="{ \"password_hash\":\"my new l33t password\" }"
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')


```
> Response Example

```
[
  {
    "id": 4,
    "username": "Trunc",
    "password_hash": "$2a$..ba",
    "email": "josh@coindroids.com"
  }
]
```

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>

### Response Details

|Name|Data Type| Description|
|---|---|---|
|id|Whole Number|The players ID #|
|username|String| The players username|
|email|String[]|An array of email addresses owned by the player|
|password_hash|String|The hash of the current password recognized by coindroids| 

