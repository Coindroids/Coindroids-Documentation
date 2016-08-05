## /mempool

> Grab a list of the actions pending for inclusion in a block, specifically for XTN (currency 1)

```shell
curl -X "GET" "https://api.coindroids.com/mempool?currency_id=eq.1" 
```

```javascript
// My Events (GET https://api.coindroids.com/mempool)

jQuery.ajax({
    url: "https://api.coindroids.com/event",
    type: "GET",
    data: {
        "currency_id": "1",
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
    # GET https://api.coindroids.com/mempool

    try:
        response = requests.get(
            url="https://api.coindroids.com/mempool",
            params={
                "currency_id": "1",
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
    "txid": "a81b5996f2cc956621989749935fa176735ef9d6dd900546e983153052d0b5e3",
    "tx_vout": 0,
    "action_type": "Attack",
    "currency_id": 2,
    "involved_droids": [
      4,
      58
    ],
    "player_id": 4,
    "player_username": "Trunc",
    "droid_id": 44,
    "droid_name": "Shelly",
    "actor": {
      "id": 44,
      "name": "Shelly",
      "avatar_links": [
        "img.jpg",
        "img.png"
      ]
    },
    "target": {
      "id": 58,
      "name": "Handsy",
      "avatar_links": [
        "img.jpg",
        "img.png"
      ]
    },
    "value": 1190000,
    "timestamp": "2016-08-01T05:29:55.893535+00:00"
  }
]
```

The mempool endpoint is used to retrieve actions pending for unconfirmed transactions. It's accuracy is not guaranteed. 

### Response Details

|Name|Data Type|Description|
|---|---|---|
|currency_id| Whole Number||
|txid|String||
|tx_vout|Whole Number||
|action_type| Action Type | _see data type for options_ |
|value| Whole Number| |
|player_id | Whole Number| The player of the droid who initiated the action|
|player_username| String | The username of the player who initiated the action |
|involved_droids| DroidIDs[] | An array of all the droids involved in teh action. |
|droid_id|Whole Number | The droid who initiated the action |
|droid_name|String | The name of the droid who initiated the action |
|actor | Short Object | The target of the action, either another droid or an item |
|target | Short Object | The name of the target. Currently only when the target is a droid |
|timestamp | Timestamp | When the action happened |


TODO: Explain the Actions and Outcomes

### Action Types

|Action|Description|
|---|---|
|Item Equip||
|Purse Filling||
|Item Use||
|Deficit||
|Droid Destruction||
|Attack||
|Ammunition Spillage||
|Registration||
|Item Purchase||
|Change||
|Droid Level-Up||
|Droid Resurrection||
 
