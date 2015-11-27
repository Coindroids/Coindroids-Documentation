---
title: Player Profile
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Interacting with the Event object through the REST API"

---

Authorization is required for requests to the /profile endpoint.



## Response Details

|Name|Data Type|Description|
|---|---|---|
| username | String | The players username|
| password_hash | String | This value is empty during a select but can be updated |
| email | String | The users email account |

## Examples


### HTTP Request

#### Retrieving current Profile Settings

```HTTP
GET https://api.coindroids.com/profile
```

#### Updating a Profile Setting

```HTTP
PATCH https://api.coindroids.com/profile
{  
	"password_hash":"somethingelse",
	"email":"my_new_email@addresses.com"
}
```

### Javascript

```javascript

// Updating a password or email (PATCH http://104.37.194.182:3000/profile)

jQuery.ajax({
    url: "http://104.37.194.182:3000/profile",
    type: "PATCH",
    headers: {
        "Authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9....C-FoIbJJxw2I",
    },
    processData: false,
    data: "{  
	\"password_hash\":\"somethingelse\"
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
    # Updating a password or email
    # PATCH http://104.37.194.182:3000/profile

    try:
        response = requests.patch(
            url="http://104.37.194.182:3000/profile",
            headers={
                "Authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6.....un0JC-FoIbJJxw2I",
            },
            data="{  
	\"password_hash\":\"somethingelse\"
}"
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')


```



