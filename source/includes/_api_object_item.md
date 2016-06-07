## /item

```javascript
// My Events (GET https://api.coindroids.com/item)

jQuery.ajax({
    url: "https://api.coindroids.com/item",
    type: "GET",
    data: {
        "id": "eq.8",
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
    # GET https://api.coindroids.com/item

    try:
        response = requests.get(
            url="https://api.coindroids.com/item",
            params={
                "id": "eq.8",
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
curl -X "GET" "https://api.coindroids.com/item?id=eq.8"
```

> Response Example

```
[
  {
    "id": 8,
    "name": "Health Pack 10",
    "item_type": "Consumable",
    "model": null,
    "class": "Assault",
    "description": "",
    "image": "",
    "level_required": 1,
    "coordinate_z": null,
    "details": {
      "health_increase": 10
    },
    "pricing": [
      {
        "currency_name": "Bitcoin Testnet",
        "address": "2Mz3osUdfVhGsgMygvGmnmfubspifkxhWXz",
        "amount": 500000
      }
    ]
  }
]
```

### Response Details

|Name|Data Type|Description|
|---|-------|-------|
|id| Whole Number| The unique numeric identifier |
|name| String| The name of the item |
|item_type| Item Type | See the item_type data type |
|description| String | A description of the item |
|image| URL | |
|level_required| Whole Number| The level a driod must be to equip or use this item|
|details| JSONB | _See Item Details below_ |
|pricing| Payment Option[] | A list of prices per available currency |
