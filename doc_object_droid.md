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

## Example

### Request

```HTTP
GET /droid?name=eq.cmdr HTTP/1.1
Host: api.coindroids.com:3000
Connection: close
User-Agent: YourBrowser
```

### Response header

```HTTP
HTTP/1.1 200 OK
transfer-encoding: chunked
Date: Sun, 22 Nov 2015 01:56:37 GMT
Server: postgrest/0.3.0.0
Content-Type: application/json
Content-Range: 0-0/1
Content-Location: /droid?name=eq.cmdr
```

### Response Body
```JSON
[
  {
    "id": 2,
    "name": "cmdr",
    "droid_class": "Heavy",
    "player_id": 1,
    "username": "Abstrct",
    "attack_address": "2NBUmB3eDawHHtz7EfMmr924yMnER78ATSf",
    "primary_ammunition_clip": "mojgvBbyPsp8B6t8nfzBL4Ui6c4Z7FhZFb",
    "additional_ammunition_clips": null,
    "level": 1,
    "experience": 0,
    "health_current": 100,
    "health_max": 100,
    "purse_current": 0,
    "purse_max": 1000000,
    "is_npc": false,
    "is_active": true,
    "last_attack": null,
    "build": [
      {
        "item_id": 1,
        "name": "4Score Armament",
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
        "item_id": 2,
        "name": "4Score Arms",
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
        "item_id": 3,
        "name": "4Score Legs",
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
        "item_id": 4,
        "name": "4Score Model Bonus",
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
        "item_id": 5,
        "name": "4Score Torso",
        "class_name": "1",
        "item_type": "Torso",
        "description": "",
        "image": "4Score",
        "cost": 69400,
        "level_required": 65,
        "damage": 0,
        "accuracy": 0,
        "defense": 65,
        "evasion": 0,
        "counter_attack": 0,
        "health_increase": 0,
        "lasts": 0,
        "stages": 0,
        "stage_damage_modifier": 0,
        "equip_scope": "Class"
      },
      {
        "item_id": 177,
        "name": "No Weapon",
        "class_name": null,
        "item_type": "Primary Weapon",
        "description": "You are literally just throwing coins, but it is a robotic throw.",
        "image": "",
        "cost": 0,
        "level_required": 1,
        "damage": 8,
        "accuracy": 0.5,
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
    "inventory": null
  }
]
```
