## /mempool

> Grab a list of the actions pending for inclusion in a block, specifically for LTC (currency 4)

```shell
curl -X "GET" "https://api.coindroids.com/mempool?currency_id=eq.4" 
```

```javascript
// Mempool (GET https://api.coindroids.com/mempool)

jQuery.ajax({
    url: "https://api.coindroids.com/mempool",
    type: "GET",
    data: {
        "currency_id": "4",
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
    # Mempool
    # GET https://api.coindroids.com/mempool

    try:
        response = requests.get(
            url="https://api.coindroids.com/mempool",
            params={
                "currency_id": "4",
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
    "txid": "d975668b75106dd58df62c8acd673e0022ddd6861fba134eadcdbea9366420b5",
    "tx_vout": 1,
    "action_type": "Attack",
    "currency_id": 4,
    "involved_droids": [
      17,
      36
    ],
    "player_id": 1,
    "player_username": "Abstrct",
    "droid_id": 17,
    "droid_name": "Cmdr",
    "actor": {
      "id": 17,
      "name": "Cmdr",
    },
    "target": {
      "id": 36,
      "name": "coblee",
    },
    "value": 1215000,
    "timestamp": "2017-04-07T15:26:29.189017+00:00"
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
 
