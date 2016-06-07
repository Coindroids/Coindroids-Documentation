## /event

> Grab the latest ten events

```shell
curl -X "GET" "https://api.coindroids.com/event?order=block_height.desc" \
	-H "Range: 0-10"
```

```javascript
// My Events (GET https://api.coindroids.com/event)

jQuery.ajax({
    url: "https://api.coindroids.com/event",
    type: "GET",
    data: {
        "order": "block_height.desc",
    },
    headers: {
        "Range": "0-10",
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
    # GET https://api.coindroids.com/event

    try:
        response = requests.get(
            url="https://api.coindroids.com/event",
            params={
                "order": "block_height.desc",
            },
            headers={
                "Range": "0-10",
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
    "currency_id": 1,
    "block_hash": "00000000420931a23a242a1ed9f57709e5e1c435f540165e523f95728a9a1878",
    "block_height": 632322,
    "txid": "be6a3d11741b5903a5c5ca296bf2bd0f48e2a71d73bb83dd0b3d9cd0a20fa901",
    "action_id": 65373,
    "is_orphaned": false,
    "tx_vout": 0,
    "action_type": "Attack",
    "player_id": 4,
    "player_username": "Trunc",
    "droid_id": 4,
    "droid_name": "Trunk",
    "target_id": 17,
    "target_name": "autotigger",
    "value": 22344600,
    "timestamp": "2016-01-09T22:34:16.755158+00:00",
    "outcomes": [
      {
        "outcome_id": 9867,
        "player_id": 22,
        "droid_id": 17,
        "outcome_type": "Purse gain",
        "value_from": null,
        "value_to": 5586150,
        "is_orphaned": false
      },
      {
        "outcome_id": 9868,
        "player_id": 4,
        "droid_id": 4,
        "outcome_type": "Ammunition spillage",
        "value_from": null,
        "value_to": 16535004,
        "is_orphaned": false
      },
      {
        "outcome_id": 9869,
        "player_id": 4,
        "droid_id": 4,
        "outcome_type": "Service fee",
        "value_from": null,
        "value_to": 223446,
        "is_orphaned": false
      },
      {
        "outcome_id": 9870,
        "player_id": 4,
        "droid_id": 4,
        "outcome_type": "Gross damage performed",
        "value_from": null,
        "value_to": 782954784,
        "is_orphaned": false
      },
      {
        "outcome_id": 9871,
        "player_id": 22,
        "droid_id": 17,
        "outcome_type": "Net damage taken",
        "value_from": null,
        "value_to": 759466140,
        "is_orphaned": false
      },
      {
        "outcome_id": 9872,
        "player_id": 4,
        "droid_id": 4,
        "outcome_type": "Experience earned",
        "value_from": null,
        "value_to": 272,
        "is_orphaned": false
      },
      {
        "outcome_id": 9873,
        "player_id": 22,
        "droid_id": 17,
        "outcome_type": "Purse changed",
        "value_from": 1000385,
        "value_to": 1000450,
        "is_orphaned": false
      },
      {
        "outcome_id": 9874,
        "player_id": 22,
        "droid_id": 17,
        "outcome_type": "Purse overage",
        "value_from": null,
        "value_to": 5586085,
        "is_orphaned": false
      },
      {
        "outcome_id": 9875,
        "player_id": 22,
        "droid_id": 17,
        "outcome_type": "Health changed",
        "value_from": 2000770,
        "value_to": 0,
        "is_orphaned": false
      },
      {
        "outcome_id": 9876,
        "player_id": 22,
        "droid_id": 17,
        "outcome_type": "Droid destroyed",
        "value_from": null,
        "value_to": null,
        "is_orphaned": false
      },
      {
        "outcome_id": 9877,
        "player_id": 4,
        "droid_id": 4,
        "outcome_type": "Experience earned",
        "value_from": null,
        "value_to": 26765,
        "is_orphaned": false
      },
      {
        "outcome_id": 9878,
        "player_id": 22,
        "droid_id": 17,
        "outcome_type": "Purse changed",
        "value_from": 1000450,
        "value_to": 0,
        "is_orphaned": false
      },
      {
        "outcome_id": 9903,
        "player_id": 4,
        "droid_id": 4,
        "outcome_type": "Experience changed",
        "value_from": 464386,
        "value_to": 491423,
        "is_orphaned": false
      },
      {
        "outcome_id": 9903,
        "player_id": 4,
        "droid_id": 4,
        "outcome_type": "Experience changed",
        "value_from": 464386,
        "value_to": 491423,
        "is_orphaned": false
      }
    ],
    "payouts": [
      {
        "payout_id": 1510,
        "currency_id": 1,
        "player_id": 17,
        "address": "mzu6WxrgEE5vM9DNbXBN4y29s4qPYEgX6Y",
        "amount": 5586085,
        "settlement_txid": "7278c3806241c985febd819532c117c47c51dcca6e544f6c414c0be739316ac1"
      },
      {
        "payout_id": 1511,
        "currency_id": 1,
        "player_id": 4,
        "address": "msHz1TmNBWdGgXMJjPMuoDjesZzM5sPKXD",
        "amount": 1000450,
        "settlement_txid": "7278c3806241c985febd819532c117c47c51dcca6e544f6c414c0be739316ac1"
      }
    ]
  }
]
```

The event endpoint is used to retreive the outcome of all actions that have taken place. 

### Response Details

|Name|Data Type|Description|
|---|---|---|
|action_id| Whole Number ||
|currency_id| Whole Number||
|block_hash|String||
|block_height|Whole Number||
|txid|String||
|tx_vout|Whole Number||
|action_type| Action Type | _see data type for options_ |
|value| Whole Number| |
|player_id | Whole Number| The player of the droid who initiated the action|
|player_username| String | The username of the player who initiated the action |
|droid_id|Whole Number | The droid who initiated the action |
|droid_name|String | The name of the droid who initiated the action |
|target_id | Whole Number | The target of the action, either another droid or an item |
|target_name | String | The name of the target. Currently only when the target is a droid |
|outcomes| Compact Outcomes[] | An array containing all the related outcomes that occured as result of the action. |
|payouts | Compact Payouts[] | An array containing all the related payouts that ocurred as a result of the action. Actions may share payouts with other actions.  
|is_orphaned| Boolean ||
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
 
### Outcome Types

|Outcome|Description|
|---|---|
|Droid destroyed||
|Rebuild successful||
|Insufficent funds sent||
|Garage inventory deposit||
|Gross damage performed||
|Refund of overpayment||
|Max purse changed||
|Payout adjustment||
|Material gained||
|Purse changed||
|Unregistered play||
|Ammunition spillage||
|Equipment changed||
|Refund of full amount||
|Garage inventory withdrawal||
|Experience earned||
|Bad aim||
|Address in use||
|Purse overage||
|Attack evaded||
|Purse gain||
|Rebuild failed||
|Clip size exceeded||
|Payout address change||
|Service fee||
|Level changed||
|Address claim||
|Attack amount above system max||
|Droid registered||
|Dust donation||
|Garnishment of deficit||
|Health changed||
|Max health changed||
|Net damage taken||
|Experience changed||
