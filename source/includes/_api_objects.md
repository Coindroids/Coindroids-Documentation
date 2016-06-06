

# API Objects


|Object | Endpoint |
|---|---|
|Currency | /currency |
|Droid | /droid |
|Event | /event |
|Garage | /garage |
|Item | /item |
|Payout | /payout |
|Player | /player | 
|Profile | /profile |


## /currency

```javascript
// View specific currency (GET https://api.coindroids.com/currency)

jQuery.ajax({
    url: "https://api.coindroids.com/currency",
    type: "GET",
    data: {
        "netcode": "eq.BTC",
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
    # View specific currency
    # GET https://api.coindroids.com/currency

    try:
        response = requests.get(
            url="https://api.coindroids.com/currency",
            params={
                "netcode": "eq.BTC",
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
curl -X "GET" "https://api.coindroids.com/currency?netcode=eq.BTC"
```

> The JSON returned will be formatted as: 

```
[
  {
    "id": 1,
    "name": "Bitcoin Testnet",
    "starting_height": 625484,
    "netcode": "XTN",
    "min_attack_size": 10000,
    "max_attack_size": 314159265,
    "registration_fee": 10000,
    "satoshis_per_coin": 100000000,
    "transaction_fee_per_byte": 75,
    "max_payouts_per_settlement": 250,
    "min_change_amount": 1000000,
    "last_ingested": {
      "block_id": 9006,
      "currency_id": 1,
      "block_hash": "000000008991c4654c715cd5aee7fdabe578e122750d588c411c0c8fb70789c8",
      "last_block_hash": "00000000a788ef252b103ebaf5de4ad6c4384cfa5537854ac8b2f38a37eb97ef",
      "height": 632282,
      "version": 4,
      "mined_time": "2016-01-09T10:26:34+00:00"
    },
    "largest_payout": 1249990000,
    "overall_purse_sum": 2446368,
    "total_number_of_attacks": 421,
    "total_amount_of_attacks": 3274158643,
    "total_number_of_item_purchases": 24,
    "total_droids": 15,
    "percentage_of_droids": 0.88235294117647058824
  }
]
```


This endpoint gives you full access to all the currency related data.


### Response Details

|Name             |Data Type     |Description            |
------------------|--------------|-----------------------|
|id               | Whole Number | The ID of the Currency|
|name             | String       | The science-given name of the Currency |
|netcode		  | String		 | A small call-sign used by the currency |
|min_attack_size  | Satoshi | The minimum number of satoshis required for an attack. Smaller amounts are considered donations. |
|max_attack_size  | Satoshi | The maximum number of satoshis that will be recognized as a valid attack. Larger attacks will be returned. |
|registration_fee | Satoshi | The number of satoshis required to register a droid under this currency |
|satoshis_per_coin| Satoshi | The amount of satoshis in one coin|
|transaction_fee_per_byte | Whole Number | The amount of fee added per byte of the transaction |
|max_payouts_per_settlement | Whole Number | The max number of settlement outputs allowed in each transaction |
|min_change_amonunt | Whole Number | The minimum number of satoshis added to a transaction as change |
|last_ingested | Block&nbsp;(Condensed&nbsp;Object) | Block details about the last block ingested and processed into the system |
|largest_payout | Satoshi | The lagest payout sent out in the currency. Currently includes payouts returned due to voided actions (Unregistered play, Max attack amount, Item overage, etc )|
|overall_purse_sum| Satoshi | The amount currently found across all available purses |
|total_number_of_attacks| Whole Number | The total number of attacks taken place on this currency. Currently includes voided attacks|
|total_amonunt_of_attacks| Satoshi |  The total sum of transaction amounts sent as attacks on this currency. Currently includes voided attacks|
|total_number_of_item_purchases | Whole Number | The total number of item purchases actions taken place on this currency. Currently includes voided purchases|
|total_droids| Whole Number | Total total number of droids playing under this currency |
|percentage_of_droids| Numeric | The percantage of droids fighting under this currency compared to others |



## /droid

```javascript
// View specific droid (GET https://api.coindroids.com/droid)

jQuery.ajax({
    url: "https://api.coindroids.com/droid",
    type: "GET",
    data: {
        "name": "eq.cmdr",
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
    try:
        response = requests.get(
            url="https://api.coindroids.com/droid",
            params={
                "name": "eq.cmdr",
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
curl -X "GET" "https://api.coindroids.com/droid?name=eq.Trunk"
```

> The JSON returned will be formatted as: 

```
[
  {
    "id": 4,
    "name": "Trunk",
    "currency_id": 1,
    "currency_code": "XTN",
    "player_id": 4,
    "username": "Trunc",
    "attack_address": "2N7LDd3GTKYBZtgnMBhBoQ4CwAU2szueptS",
    "primary_ammunition_clip": "msHz1TmNBWdGgXMJjPMuoDjesZzM5sPKXD",
    "additional_ammunition_clips": [
      "mxtdvzXLoiHsv9EHrPuqkVFdLXx9mRfrJc",
      "myGqyTqViDQSLnq9p16FZQQw1PtK4jzA7h"
    ],
    "level": 2,
    "experience": 629,
    "health_current": 50,
    "health_max": 50,
    "purse_current": 7066014,
    "is_npc": false,
    "is_active": true,
    "last_attack": 868029,
    "death_height": null,
    "is_dead": false,
    "created_at": "2015-12-16T03:27:08.798193+00:00",
    "build": [
        {"name": "Tank Training Arm","class": "Tank","image": "","model": "Tank Training","details": { "ems": 0,"defense": 0,"drop_scope": "Drone","composition": {"73": [ 0.01875],"74": [ 0.0125],"75": [ 0.075],"76": [ 0.0125],"77": [ 0.00625]},"equip_scope": "Class","drop_frequency": 0.01,"equip_optional": "","equip_required": "","defense_at_unlock": 0,"material_strength": 0,"defense_set_percentage": 0.1},"item_id": 12,"item_type": "Arm","description": "","coordinate_z": null,"level_required": 0,"real_item_type": "Arm"},
        {"name": "Tank Training Arm","class": "Tank","image": "","model": "Tank Training","details": {"ems": 0,"defense": 0,"drop_scope": "Drone","composition": {"73": [ 0.01875],"74": [ 0.0125],"75": [ 0.075],"76": [ 0.0125],"77": [ 0.00625]},"equip_scope": "Class","drop_frequency": 0.01,"equip_optional": "","equip_required": "","defense_at_unlock": 0,"material_strength": 0,"defense_set_percentage": 0.1},"item_id": 12,"item_type": "Arm","description": "","coordinate_z": null,"level_required": 0,"real_item_type": "Arm"},
        {"name": "Tank Training Leg","class": "Tank","image": "","model": "Tank Training","details": {"ems": 0,"defense": 0,"drop_scope": "Drone","composition": {"73": [ 0.0375],"74": [ 0.025],"75": [ 0.15],"76": [ 0.025],"77": [ 0.0125]},"equip_scope": "Class","drop_frequency": 0.01,"equip_optional": "","equip_required": "","defense_at_unlock": 0,"material_strength": 0,"defense_set_percentage": 0.3},"item_id": 14,"item_type": "Leg","description": "","coordinate_z": null,"level_required": 0,"real_item_type": "Leg"},
        {"name": "Tank Training Head","class": "Tank","image": "","model": "Tank Training","details": {"ems": 0,"defense": 0,"drop_scope": "Drone","composition": {"73": [ 0.015],"74": [ 0.01],"75": [ 0.06],"76": [ 0.01],"77": [ 0.005]},"equip_scope": "Class","drop_frequency": 0.01,"equip_optional": "","equip_required": "","defense_at_unlock": 0,"material_strength": 0,"defense_set_percentage": 0.1},"item_id": 13,"item_type": "Head","description": "","coordinate_z": null,"level_required": 0,"real_item_type": "Head"},
        {"name": "Tank Training Torso","class": "Tank","image": "","model": "Tank Training","details": {"ems": 0,"defense": 0,"drop_scope": "Drone","composition": {"73": [ 0.06],"74": [ 0.04],"75": [ 0.24],"76": [ 0.04],"77": [ 0.02]},"equip_scope": "Class","drop_frequency": 0.01,"equip_optional": "{Shield}","equip_required": "{Arm,Arm,Leg,Head,Weapon}","defense_at_unlock": 0,"material_strength": 0,"defense_set_percentage": 0.4},"item_id": 27,"item_type": "Torso","description": "","coordinate_z": null,"level_required": 0,"real_item_type": "Torso"},
        {"name": "Tank Training No Weapon","class": "Tank","image": "","model": "Tank Training","details": {"ems": 0,"damage": 1,"accuracy": 0.5,"clip_size": 1,"drop_scope": "Never","composition": "","equip_scope": "Class","drop_frequency": 0,"equip_optional": "","equip_required": "","accuracy_likely": 0.75,"material_strength": 0},"item_id": 28,"item_type": "Weapon","description": "","coordinate_z": null,"level_required": 0,"real_item_type": "Weapon"}
    ],
    "attribute": {"ems": "0","damage": "2.00000000000000000000","defense": "0.20000000000000000000","accuracy": "0.5","clip_size": "1000000","base_damage": "1","weapon_unlock": "0","accuracy_likely": "0.75" },
    "composition": {"73": [  0.01875,  0.01875,  0.0375,  0.015,  0.06],"74": [  0.0125,  0.0125,  0.025,  0.01,  0.04],"75": [  0.075,  0.075,  0.15,  0.06,  0.24],"76": [  0.0125,  0.0125,  0.025,  0.01,  0.04],"77": [  0.00625,  0.00625,  0.0125,  0.005,  0.02] },
    "pending_build": null,
    "currency_in": 2956900459,
    "currency_out": 2228644333,
    "highest_payout": 396170029,
    "attacks": 285,
    "targeted": 57,
    "deaths": 29,
    "defensive_evasions": 2,
    "offensive_evasions": 0,
    "average_damage_performed": 49438751.169675090253,
    "total_damage_performed": 13694534074,
    "total_damage_defended": 15999069,
    "most_targeted_id": 1,
    "most_targeted_name": "cmdr",
    "worst_enemy_id": 17,
    "worst_enemy_name": "autotigger"
  }
]
```

The heart of the Coindroids system, the /droid API endpoint. 





|Name|Data Type|Description|
---|---|---|
| id | Whole Number| The ID of the Droid|
| name | String| The science-given name of the Droid |
| player_id | Whole Number | The ID of the droids squishy overlord | 
| username | String | Name of the droids squishy overlord |
| attack_address| Cryptocurrency Address | The address other players can use to attack this droid|
| primary\_ammunition_clip| Cryptocurrency Address | The primary address used for payouts involving this droid |
| additional\_ammunition_clips | Cryptocurrency Address[] | Additional addresses tracked for droid actions involving this droid|
| level | Whole Number | The level of a droid |
| experience | Whole Number | The total experience gained by this droid to date |
| health_current | Whole Number | The current state of the health for a droid going into the next processing block|
| health_max | Whole Number | The maximum health that this droid can have |
| purse_current | Whole Number | The current state of the purse for a droid going into the next block processing|
| is_npc | Boolean | _[True, False]_ Is this human controlled or a coindroids bot instance? |
| is_active| Boolean | Has this droid been properly registered to a player wallet|
| last_attack | Whole Number | The height of the last Attack action performed by this droid|
| build | Items[] | A description of the items which make up the build of this droid |
| inventory| Items[] | A list of all active items available to the droid during the next block processing| 
| currency_in | Satoshi | Total amount of value sent to the system from this droid |
| currency_out | Satoshi | Total amount of payouts sent to this droid from the system |
| highest_payout | Satoshi | Largest payout won by the droid (currently includes refunds from voided actions)|
| attacks | Whole Number | Total number of attacks the droid has made |
| targeted | Whole Number | Total number of attacks by other droids against this droid |
| deaths| Whole Number | Total deaths this droid has experienced |
| defensive_evasions| Whole Number | Total number of times the droid was able to evade an attack |
| offensive_evasions| Whole Number | Total number of times this droids attack was evaded |
| average_damage_performed| Whole Number | Average damage done by the droid in an attack |
| total_damage_performed| Whole Number | Total damage performed by this droid across all attacks |
| total_damage_defended| Whole Number | Total damage defended against by this droid across all attacks against it |
| most_targeted_id| Whole Number | The target this droid attacks most often |
| most_targeted_name | String | The name of the target this droid attacks most often |
| worst_enemy_id| Whole Number | The droid that targets this droid the most |
| worst_enemy_name | String | The name of the droid that targets this droid the most |

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

## /payout

> Grab the 4 latest payouts

```javascript
// My Events (GET https://api.coindroids.com/payout)

jQuery.ajax({
    url: "https://api.coindroids.com/payout",
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
    # GET https://api.coindroids.com/payout

    try:
        response = requests.get(
            url="https://api.coindroids.com/payout",
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

```shell
curl -X "GET" "https://api.coindroids.com/payout?order=block_height.desc" \
	-H "Range: 0-10"

```


> Response Example

```
[
  {
    "currency": "Bitcoin Testnet",
    "block_height": 868029,
    "actions": [
      "Attack"
    ],
    "outcome_type": "Refund of overpayment",
    "amount": 0.00700000000000000000,
    "player": "Trunc",
    "droid": "Trunk"
  },
  {
    "currency": "Bitcoin Testnet",
    "block_height": 868029,
    "actions": [
      "Attack"
    ],
    "outcome_type": "Refund of overpayment",
    "amount": 0.00410000000000000000,
    "player": "Trunc",
    "droid": "Trunk"
  },
  {
    "currency": "Bitcoin Testnet",
    "block_height": 868029,
    "actions": [
      "Attack",
      "Attack"
    ],
    "outcome_type": "Droid destroyed",
    "amount": 0.07186051000000000000,
    "player": "Trogdor",
    "droid": "Trogdor1"
  },
  {
    "currency": "Bitcoin Testnet",
    "block_height": 868028,
    "actions": [
      "Attack",
      "Attack",
      "Attack"
    ],
    "outcome_type": "Droid destroyed",
    "amount": 0.0000000000000000000000000000,
    "player": "Trunc",
    "droid": "Rob1t"
  }
]
```

A list of all the payouts going out of the system. 

### Response 

|Name|Type|Description|
|---|---|---|
|currency|String|The name of the currency network the payout was sent on|
|block_height|Whole Number|The height of the block it was included in|
|actions|Action Type[]|The action type(s) that triggered the payout|
|outcome_type|Outcome Type[]|The outcome type(s) that triggered the payout|
|amount|Numeric|The amount sent out|
|player|String|The name of the player who received the payout (where applicable)|
|droid|String|The name of the Droid who received the payout (where applicable)|
 


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

