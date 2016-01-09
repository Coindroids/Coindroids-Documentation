---
title: Droids
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Interacting with the Droid object through the REST API"

---

## Request

```HTTP
GET https://api.coindroids.com/droid
```

## Response Details

|Name|Data Type|Description|
---|---|---|
| id | Whole Number| The ID of the Droid|
| name | String| The science-given name of the Droid |
| droid_class| String | _[Heavy, Infantry, Rogue]_
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
| purse_max |Whole Number|The maximum purse that this droid can have. All overage is forwarded on to the droids primary address. |
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


## Examples

### Javascript

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

### Python

```python
# Install the Python Requests library:
# `pip install requests`

import requests


def send_request():
    # View specific droid
    # GET https://api.coindroids.com/droid

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

### HTTP Request

#### Request

```HTTP
GET /droid?name=eq.Trunk HTTP/1.1
Host: api.coindroids.com
Connection: close
User-Agent: YourBrowser
```

#### Response header

```HTTP
HTTP/1.1 200 OK
transfer-encoding: chunked
Date: Sun, 22 Nov 2015 01:56:37 GMT
Server: postgrest/0.3.0.0
Content-Type: application/json
Content-Range: 0-0/1
Content-Location: /droid?name=eq.Trunk
```

#### Response Body
```JSON
[
  {
    "id": 4,
    "name": "Trunk",
    "currency_id": 1,
    "currency_code": "XTN",
    "droid_class": "Assault",
    "droid_model_image": "TheTruncator",
    "droid_model_name": "The Truncator",
    "player_id": 4,
    "username": "Trunc",
    "attack_address": "2N7LDd3GTKYBZtgnMBhBoQ4CwAU2szueptS",
    "primary_ammunition_clip": "msHz1TmNBWdGgXMJjPMuoDjesZzM5sPKXD",
    "additional_ammunition_clips": [
      "mxtdvzXLoiHsv9EHrPuqkVFdLXx9mRfrJc",
      "mwdKDu3LjyYFQyYMBuLtYJKybPF4eRozJS",
      "mgfyzBQLL5wiqK1tXiDhH1MStvYrk64jF8"
    ],
    "level": 14,
    "experience": 491423,
    "health_current": 2001040,
    "health_max": 2001040,
    "purse_current": 1000520,
    "purse_max": 1000520,
    "is_npc": false,
    "is_active": true,
    "last_attack": 632322,
    "created_at": "2015-12-16T03:27:08.798193+00:00",
    "build": [
      {
        "item_id": 255,
        "name": "The Truncator Armament",
        "class_name": "1",
        "item_type": "Armament",
        "description": "",
        "image": "",
        "cost": 0,
        "level_required": 0,
        "damage": 0,
        "accuracy": 0,
        "defense": 0,
        "evasion": 0,
        "counter_attack": 0,
        "health_increase": 0,
        "lasts": 0,
        "stages": 0,
        "stage_damage_modifier": 0,
        "equip_scope": "Class"
      },
      {
        "item_id": 256,
        "name": "The Truncator Arms",
        "class_name": "1",
        "item_type": "Arms",
        "description": "",
        "image": "",
        "cost": 0,
        "level_required": 0,
        "damage": 0,
        "accuracy": 0,
        "defense": 0,
        "evasion": 0,
        "counter_attack": 0,
        "health_increase": 0,
        "lasts": 0,
        "stages": 0,
        "stage_damage_modifier": 0,
        "equip_scope": "Class"
      },
      {
        "item_id": 257,
        "name": "The Truncator Head",
        "class_name": "1",
        "item_type": "Head",
        "description": "",
        "image": "",
        "cost": 0,
        "level_required": 0,
        "damage": 0,
        "accuracy": 0,
        "defense": 0,
        "evasion": 0,
        "counter_attack": 0,
        "health_increase": 0,
        "lasts": 0,
        "stages": 0,
        "stage_damage_modifier": 0,
        "equip_scope": "Class"
      },
      {
        "item_id": 258,
        "name": "The Truncator Legs",
        "class_name": "1",
        "item_type": "Legs",
        "description": "",
        "image": "",
        "cost": 0,
        "level_required": 0,
        "damage": 0,
        "accuracy": 0,
        "defense": 0,
        "evasion": 0,
        "counter_attack": 0,
        "health_increase": 0,
        "lasts": 0,
        "stages": 0,
        "stage_damage_modifier": 0,
        "equip_scope": "Class"
      },
      {
        "item_id": 259,
        "name": "The Truncator Model Bonus",
        "class_name": "1",
        "item_type": "Model Bonus",
        "description": "",
        "image": "",
        "cost": 0,
        "level_required": 0,
        "damage": 0,
        "accuracy": 0,
        "defense": 0,
        "evasion": 0,
        "counter_attack": 0,
        "health_increase": 0,
        "lasts": 0,
        "stages": 0,
        "stage_damage_modifier": 0,
        "equip_scope": "Model"
      },
      {
        "item_id": 260,
        "name": "The Truncator Torso",
        "class_name": "1",
        "item_type": "Torso",
        "description": "",
        "image": "TheTruncator",
        "cost": 0,
        "level_required": null,
        "damage": 0,
        "accuracy": 0,
        "defense": 75,
        "evasion": 0,
        "counter_attack": 0,
        "health_increase": 0,
        "lasts": 0,
        "stages": 0,
        "stage_damage_modifier": 0,
        "equip_scope": "Class"
      },
      {
        "item_id": 111,
        "name": "Dual Disc Launchers",
        "class_name": null,
        "item_type": "Primary Weapon",
        "description": "Akimbo baby!",
        "image": "",
        "cost": 200,
        "level_required": 8,
        "damage": 20,
        "accuracy": 0.63,
        "defense": 0,
        "evasion": 0,
        "counter_attack": 0,
        "health_increase": 0,
        "lasts": 0,
        "stages": 0,
        "stage_damage_modifier": 0,
        "equip_scope": "Global"
      },
      {
        "item_id": 227,
        "name": "Shoulder Mounted Disc Launcher",
        "class_name": null,
        "item_type": "Secondary Weapon",
        "description": "Unsurprisingly it's a disc launcher mounted on your shoulder.",
        "image": "",
        "cost": 200,
        "level_required": 6,
        "damage": 10,
        "accuracy": 0.58,
        "defense": 0,
        "evasion": 0,
        "counter_attack": 0,
        "health_increase": 0,
        "lasts": 0,
        "stages": 0,
        "stage_damage_modifier": 0,
        "equip_scope": "Global"
      }
    ],
    "inventory": null,
    "currency_in": 2485438439,
    "currency_out": 2025249796,
    "highest_payout": 396170029,
    "attacks": 151,
    "targeted": 40,
    "deaths": 19,
    "defensive_evasions": 2,
    "offensive_evasions": 0,
    "average_damage_performed": 45924520.761904761905,
    "total_damage_performed": 6750904552,
    "total_damage_defended": 7078294,
    "most_targeted_id": 1,
    "most_targeted_name": "cmdr",
    "worst_enemy_id": 2,
    "worst_enemy_name": "TigerBot"
  }
]
```
