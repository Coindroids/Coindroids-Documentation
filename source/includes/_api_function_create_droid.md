## /rpc/create_droid

```shell
curl -X "POST" "https://api.coindroids.com/rpc/create_droid" \
	-H "Authorization: Bearer eyJhbGciO...DSzsybGFgk" \
	-H "Content-Type: application/json" \
	-d "{\"name\":\"Droidy McDroidface\",\"currency_id\":\"1\",\"model\":\"Assault Training\"}"
```

```javascript
jQuery.ajax({
    url: "https://api.coindroids.com//rpc/create_droid",
    type: "POST",
    headers: {
        "Authorization": "Bearer eyJhbGc...sybGFgk",
        "Content-Type": "application/json",
    },
    contentType: "application/json",
    data: JSON.stringify({
        "name": "Droidy McDroidface",
        "model": "Assault Training",
        "currency_id": "1"
    })
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
import json


def send_request():
  try:
        response = requests.post(
            url="https://api.coindroids.com/rpc/create_droid",
            headers={
                "Authorization": "Bearer eyJhbGciOiJI...zsybGFgk",
                "Content-Type": "application/json",
            },
            data=json.dumps({
                "name": "Droidy McDroidface",
                "model": "Droidy McDroidface",
                "currency_id": "1"
            })
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')
```

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>


### Parameters

|Name | Type | Description|
|----|----|---|
|name | CHARACTER VARYING| Your droids new classy moniker|
|model| Model | See the list of models available for new droids below | 
|currency_id | Bigint | See the /currency endpoint for available currencies|

### Response Details

|Name | Description|
|----|----|
|Droid| The droid object as if called through the /droid endpoint. |
