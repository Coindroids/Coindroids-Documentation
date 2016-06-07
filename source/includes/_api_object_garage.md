## /garage

```javascript
// Viewing current password hash or email (GET https://api.coindroids.com/garage)

jQuery.ajax({
    url: "https://api.coindroids.com/garage",
    type: "GET",
    headers: {
        "Authorization": "Bearer eyJhbG...5iAOo",
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

```shell
curl -X "GET" "https://api.coindroids.com/garage" \
	-H "Authorization: Bearer eyJhbG...5iAOo"
```

```python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # Viewing current password hash or email
    # GET https://api.coindroids.com/garage

    try:
        response = requests.get(
            url="https://api.coindroids.com/garage",
            headers={
                "Authorization": "Bearer eyJhbG...5iAOo",
            },
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
    "quantity": 2,
    "currency_id": 1,
    "id": 12,
    "name": "Tank Training Arm",
    "description": "",
    "item_type": "Arm",
    "model": "Tank Training",
    "class": "Tank",
    "details": {
      "ems": 0,
      "defense": 0,
      "drop_scope": "Drone",
      "composition": {
        "73": [
          0.01875
        ],
        "74": [
          0.0125
        ],
        "75": [
          0.075
        ],
        "76": [
          0.0125
        ],
        "77": [
          0.00625
        ]
      },
      "equip_scope": "Class",
      "drop_frequency": 0.01,
      "equip_optional": "",
      "equip_required": "",
      "defense_at_unlock": 0,
      "material_strength": 0,
      "defense_set_percentage": 0.1
    },
    "level_required": 0
  },
  {
    "quantity": 1,
    "currency_id": 1,
    "id": 13,
    "name": "Tank Training Head",
    "description": "",
    "item_type": "Head",
    "model": "Tank Training",
    "class": "Tank",
    "details": {
      "ems": 0,
      "defense": 0,
      "drop_scope": "Drone",
      "composition": {
        "73": [
          0.015
        ],
        "74": [
          0.01
        ],
        "75": [
          0.06
        ],
        "76": [
          0.01
        ],
        "77": [
          0.005
        ]
      },
      "equip_scope": "Class",
      "drop_frequency": 0.01,
      "equip_optional": "",
      "equip_required": "",
      "defense_at_unlock": 0,
      "material_strength": 0,
      "defense_set_percentage": 0.1
    },
    "level_required": 0
  }
]
```
<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>

### Response Details

|Name|Data Type|Description|
|---|-------|-------|
|quantity|Whole Number|The amount you have access to equip|
|currency_id|Whole Number| The ID of the currency this item is associated with. Items cannot jump currency realms|
|id|Whole Number| The ID of the item|
|name|String| The name of the object|
|...|...|...|
