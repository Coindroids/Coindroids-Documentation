## /player

> Find the 5 newest players

```javascript
// My Events (GET https://api.coindroids.com/player)

jQuery.ajax({
    url: "https://api.coindroids.com/player",
    type: "GET",
    data: {
        "order": "id.desc",
    },
    headers: {
        "Range": "0-4",
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
    # My Events
    # GET https://api.coindroids.com/player

    try:
        response = requests.get(
            url="https://api.coindroids.com/player",
            params={
                "order": "id.desc",
            },
            headers={
                "Range": "0-4",
            },
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')



```

```shell
curl -X "GET" "https://api.coindroids.com/player?order=id.desc" \
	-H "Range: 0-4"
```

> Response Example

```
[
  {
    "id": 23,
    "username": "BitDroid",
    "droids": [
      18
    ]
  },
  {
    "id": 22,
    "username": "autotiger",
    "droids": [
      17
    ]
  },
  {
    "id": 21,
    "username": "davidl",
    "droids": [
      16
    ]
  },
  {
    "id": 20,
    "username": "udecker",
    "droids": null
  },
  {
    "id": 19,
    "username": "phorex",
    "droids": [
      15
    ]
  }
]
```


### Response Details

|Name|Data Type| Description|
|---|---|---|
|id|Whole Number|The ID of the player account|
|username|String|The username of the player account. Not to be confused with their Droid name (although this could match)|
|droids|Whole Number[]|An array of all Droid ID #s belonging to this player|

