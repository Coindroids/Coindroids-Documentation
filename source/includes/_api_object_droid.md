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
curl -X "GET" "https://api.coindroids.com/droid?name=eq.cmdr"
```

> The JSON returned will be formatted as: 

```
[
  {
    "id": 17,
    "name": "Cmdr",
    "currency_id": 4,
    "currency_code": "LTC",
    "player_id": 1,
    "username": "Abstrct",
    "attack_address": "3QMrkxTuosoYXySct3kZxoMESDHh1uAwsZ",
    "primary_ammunition_clip": "LfK1GXhTE3hrEY9uxjxrT3T8QX18kKJBs5",
    "additional_ammunition_clips": [
      "LbwUTU7zq25EUKTaD8esVyBoZTW6qedgR8"
    ],
    "level": 2,
    "experience": 616,
    "experience_goal": 1887,
    "health_current": 50,
    "health_max": 50,
    "purse_current": 938544,
    "is_npc": false,
    "is_active": true,
    "last_attack": 1181558,
    "is_shielded": false,
    "is_covered": false,
    "death_height": null,
    "is_dead": false,
    "created_at": "2017-03-25T20:25:48.337337+00:00",
    "build": [
      {
        "name": "Assault Training Arm",
        "class": "Assault",
        "image": "",
        "model": "Assault Training",
        "details": {
          "ems": 0,
          "images": {
            "solo": {
              "large": "a_1_4x_larm.png",
              "thumb": "a_1_1x_larm.png",
              "medium": "a_1_2x_larm.png"
            },
            "equipped": {
              "large": [
                "5_a_1_4x_rarm.png",
                "2_a_1_4x_larm.png"
              ],
              "thumb": [
                "5_a_1_1x_rarm.png",
                "2_a_1_1x_larm.png"
              ],
              "medium": [
                "5_a_1_2x_rarm.png",
                "2_a_1_2x_larm.png"
              ]
            }
          },
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
          "equip_optional": [],
          "equip_required": [],
          "defense_at_unlock": 0,
          "material_strength": "",
          "defense_set_percentage": 0.1
        },
        "item_id": 1,
        "item_type": "Arm",
        "short_name": "Assault Training",
        "description": "",
        "coordinate_z": null,
        "level_required": 1,
        "real_item_type": "Arm"
      }
      // bunch commented out...
    ],
    "attribute": {
      "ems": 0,
      "class": "Assault",
      "model": "Assault Training",
      "damage": 10.2750000000000000,
      "defense": 0.13000000000000000000,
      "accuracy": 0.44,
      "blueprint": {
        "Arm": [
          1,
          1
        ],
        "Leg": [
          3,
          11
        ],
        "Head": 2,
        "Torso": 5,
        "Weapon": 7
      },
      "clip_size": 1620000,
      "base_damage": 6.85,
      "weapon_unlock": 1,
      "accuracy_likely": 0.72
    },
    "composition": {
      "73": [
        0.01875,
        0.01875,
        0.01875,
        0.01875,
        0.015,
        0.06
      ],
      "74": [
        0.0125,
        0.0125,
        0.0125,
        0.0375,
        0.01,
        0.04
      ]
    },
    "pending_build": null,
    "currency_in": 458117000,
    "currency_out": 113367420,
    "highest_payout": 27298282,
    "attacks": 311,
    "targeted": 34,
    "deaths": 3,
    "average_damage_performed": 9.3257328990228013,
    "total_damage_performed": 2863,
    "total_damage_defended": 27,
    "most_targeted_id": 25,
    "most_targeted_name": "sailias",
    "worst_enemy_id": 38,
    "worst_enemy_name": "Finite"
  }
]
```

The heart of the Coindroids system, the /droid API endpoint. 





|Name|Data Type|Description|
---|---|---|
|id | Whole Number| The ID of the Droid|
|name | String| The science-given name of the Droid |
|currency_id | Whole Number | The ID of the currency realm the droid is in|
|currency_code | Netcode | The three letter code for a currency (i.e. LTC)|
|player_id | Whole Number | The ID of the droids squishy overlord | 
|username | String | Name of the droids squishy overlord |
|attack_address| Cryptocurrency Address | The address other players can use to attack this droid|
|primary\_ammunition_clip| Cryptocurrency Address | The primary address used for payouts involving this droid |
|additional\_ammunition_clips | Cryptocurrency Address[] | Additional addresses tracked for droid actions involving this droid|
|level | Whole Number | The level of a droid |
|experience | Whole Number | The total experience gained by this droid to date |
|health_current | Whole Number | The current state of the health for a droid going into the next processing block|
|health_max | Whole Number | The maximum health that this droid can have |
|purse_current | Whole Number | The current state of the purse for a droid going into the next block processing|
|is_npc | Boolean | _[True, False]_ Is this human controlled or a coindroids bot instance? |
|is_active| Boolean | Has this droid been properly registered to a player wallet|
|is_shielded | Boolean | Is the droid currently in a Shielding status? |
|is_covered | Boolean | Is the droid currently in a Covered status? |
|death_height | Whole Number | The height in which the droid died (NULL if not currently dead)|
|is_dead| Boolean | Is the droid currently dead? |
|last_attack | Whole Number | The height of the last Attack action performed by this droid|
|created_at | Timestamp | The date and time of droid creation |
|build | Items[] | A description of the items which make up the build of this droid |
|build[].item_id | Whole Number | The ID of the item equipped in the build | 
|build[].name | String | The name of the item equipped in the build|
|build[].class | Class Type | The class of the item equipped in the build |
|build[].image | File Path | The path to the static image hosted for the item|
|build[].model | Model Type | The model of the item equipped in the build |
|build[].details | Item Details Object | The full attributes of the item equipped in the build|
|build[].item_type | Item Type | The type of the item equipped in the build |
|build[].short_name | String | A short identifier of the equipped item|
|build[].description | String | A long description of the equipped item |
|build[].level_required | Whole Number| The level that must be met for the item to be equippable|
|build[].real_item_type | String | Another Item Type field that made sense at the time but I don't quite recall why this is here|
|attribute| Attributes | The culminating stats of a droid build. Includes the following details (attribute.*)|
|attribute.ems | Numeric |Value between 0-100%, used when calculating EMI |
|attribute.class | Class Type| The resulting Class of the droid build|
|attribute.model | Model Type| The resulting Model of the droid build|
|attribute.defense| Numeric| Value between 0-100%, used during attack calculations|
|attribute.accuracy|Numeric| Value between 0-100%, used during attack calculations|
|attribute.clip_size|Whole Number| The number of bullets (i.e. Tokens) that can be fired per block |
|attribute.base_damage|Numeric|Value between 0-100%, used during attack calculations|
|attribute.weapon_unlock|Numeric|Value between 0-100%, used during attack calculations|
|attribute.accuracy_likely|Numeric|Value between 0-100%, the average accuracy to expect from the build|
|attribute.blueprint|Droid Blueprint Object| An object that denotes each item and the position it occupies on the droid|
|composition| Composition Objects|The makeup of the droids materials (composition.<item_id>.*)|
|pending_build | Build Object | The full new build of a droid including build, composition, part_list and attribute|
|currency_in | Satoshi | Total amount of value sent to the system from this droid |
|currency_out | Satoshi | Total amount of payouts sent to this droid from the system |
|highest_payout | Satoshi | Largest payout won by the droid (currently includes refunds from voided actions)|
|attacks | Whole Number | Total number of attacks the droid has made |
|targeted | Whole Number | Total number of attacks by other droids against this droid |
|deaths| Whole Number | Total deaths this droid has experienced |
|average_damage_performed| Whole Number | Average damage done by the droid in an attack |
|total_damage_performed| Whole Number | Total damage performed by this droid across all attacks |
|total_damage_defended| Whole Number | Total damage defended against by this droid across all attacks against it |
|most_targeted_id| Whole Number | The target this droid attacks most often |
|most_targeted_name | String | The name of the target this droid attacks most often |
|worst_enemy_id| Whole Number | The droid that targets this droid the most |
|worst_enemy_name | String | The name of the droid that targets this droid the most |
