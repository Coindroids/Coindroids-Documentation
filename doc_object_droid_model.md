---
title: Droid Models
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Interacting with the Droid Model object through the REST API"

---

## Request

```HTTP
GET https://api.coindroids.com/model
```

## Response Details

|Name|Data Type|Description|
|---|---|---|
| id | Whole Number| The ID of the Droid|
| name | String| The science-given name of the Droid |
|description|String|A blurb about the model|
|image| URL | |
| droid_class| String | _[Heavy, Infantry, Rogue]_
| purchase_address| Cryptocurrency Address | The address other players can use to attack this droid|
| build | Items[] | A description of the items which make up the build of this droid |

## Example

### Request

```HTTP
GET /model?name=eq.Base%20Heavy HTTP/1.1
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
Content-Location: /model?name=eq.Base%20Heavy
```

### Response Body
```JSON
[
  {
    "id": 3,
    "name": "Base Heavy",
    "description": "",
    "image": "BaseHeavy",
    "cost": 0,
    "purchase_address": "2NEUuUgHDaNotgBnQZ9m38hiyFLGB1Q1ZCW",
    "model_discount": 0.2,
    "droid_class": 1,
    "build": [
      {
        "item_id": 19,
        "name": "Base Heavy Armament",
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
        "item_id": 20,
        "name": "Base Heavy Arms",
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
        "item_id": 21,
        "name": "Base Heavy Head",
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
        "item_id": 22,
        "name": "Base Heavy Legs",
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
        "item_id": 23,
        "name": "Base Heavy Model Bonus",
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
        "item_id": 24,
        "name": "Base Heavy Torso",
        "class_name": "1",
        "item_type": "Torso",
        "description": "",
        "image": "BaseHeavy",
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
    ]
  },
  {
    "id": 3,
    "name": "Base Heavy",
    "description": "",
    "image": "BaseHeavy",
    "cost": 0,
    "purchase_address": "9xMXvcaCjnGBsaSAZjx5wEVwMKRQLkRSHD",
    "model_discount": 0.2,
    "droid_class": 1,
    "build": [
      {
        "item_id": 19,
        "name": "Base Heavy Armament",
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
        "item_id": 20,
        "name": "Base Heavy Arms",
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
        "item_id": 21,
        "name": "Base Heavy Head",
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
        "item_id": 22,
        "name": "Base Heavy Legs",
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
        "item_id": 23,
        "name": "Base Heavy Model Bonus",
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
        "item_id": 24,
        "name": "Base Heavy Torso",
        "class_name": "1",
        "item_type": "Torso",
        "description": "",
        "image": "BaseHeavy",
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
    ]
  },
  {
    "id": 3,
    "name": "Base Heavy",
    "description": "",
    "image": "BaseHeavy",
    "cost": 0,
    "purchase_address": "3KguTudVbTDQ2ci5ebKhHdKK5f8xajpWoR",
    "model_discount": 0.2,
    "droid_class": 1,
    "build": [
      {
        "item_id": 19,
        "name": "Base Heavy Armament",
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
        "item_id": 20,
        "name": "Base Heavy Arms",
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
        "item_id": 21,
        "name": "Base Heavy Head",
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
        "item_id": 22,
        "name": "Base Heavy Legs",
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
        "item_id": 23,
        "name": "Base Heavy Model Bonus",
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
        "item_id": 24,
        "name": "Base Heavy Torso",
        "class_name": "1",
        "item_type": "Torso",
        "description": "",
        "image": "BaseHeavy",
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
    ]
  }
]
```
