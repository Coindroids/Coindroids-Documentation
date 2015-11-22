---
title: Items
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: November 21, 2015
summary: "Interacting with the Items through the REST API"

---

## Request

```HTTP
GET https://api.coindroids.com/item
```

## Response Details

|Name|Data Type|Description|
|---|---|---|
|id| Whole Number| The unique numeric identifier |
|name| String| The name of the item |
|droid_class| Droid Class | _[Heavy, Infantry, Rogue]_|
|item_type| Item Type | See the item_type data type |
|description| String | A description of the item |
|image| URL | |
|level_required| Whole Number| The level a driod must be to equip or use this item|
|damage| ||
|accuracy||
|defense||
|evasion||
|counter_attack||
|health_increase||
|lasts||
|stages||
|stage_damage_modifier||
|drop_scope||
|equip_scope||
|pricing||


## Example

### Request

```HTTP
GET /item?item_type=eq.Primary%20Weapon&level_required=lt.10 HTTP/1.1
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
Content-Location: /item?item_type=eq.Primary%20Weapon&level_required=lt.10
```

### Response Body
```JSON
[
  {
    "id": 81,
    "name": "Cross Bow",
    "droid_class": null,
    "item_type": "Primary Weapon",
    "description": "In the process of making the bow powerful enough to punch through a droid's chassis the draw string cannot be drawn by hand. Yes, including robot hands. Instead it uses a silent ratcheting hand crack to set the draw string. This weapon is favoured by droid assassins as it's much quieter than a gun.",
    "image": "",
    "level_required": 9,
    "damage": 18,
    "accuracy": 0.82,
    "defense": 0,
    "evasion": 0,
    "counter_attack": 0,
    "health_increase": 0,
    "lasts": 0,
    "stages": 2,
    "stage_damage_modifier": 5,
    "drop_scope": "NPC",
    "equip_scope": "Global",
    "pricing": [
      {
        "currency_name": "Bitcoin Testnet",
        "address": "2NCAdcLzocLHivfM2tSGNRR398Ndu1uv7e7",
        "amount": 272000000
      },
      {
        "currency_name": "Defcoin Mainnet",
        "address": "AB1KNtjQtfXSP9rnGnGZWdC7oMPCo64ucM",
        "amount": 27200000000
      },
      {
        "currency_name": "Bitcoin Mainnet",
        "address": "333izUCYFHoSthVTyHsNA5nrT1WVT6Gq5a",
        "amount": 272000000
      }
    ]
  },
  {
    "id": 177,
    "name": "No Weapon",
    "droid_class": null,
    "item_type": "Primary Weapon",
    "description": "You are literally just throwing coins, but it is a robotic throw.",
    "image": "",
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
    "drop_scope": "NPC",
    "equip_scope": "Global",
    "pricing": [
      {
        "currency_name": "Bitcoin Testnet",
        "address": "2N9EWswvT4ymEenkpEEL5woytJXQGJTdtzq",
        "amount": 0
      },
      {
        "currency_name": "Defcoin Mainnet",
        "address": "A3ySzArE1UC7abWMBMhAW9rftE4dpDX4Az",
        "amount": 0
      },
      {
        "currency_name": "Bitcoin Mainnet",
        "address": "3GKBp7tjLftFe1R8qMf5xAp6Ea8hUpkLCG",
        "amount": 0
      }
    ]
  },
  {
    "id": 254,
    "name": "The Mad Cane",
    "droid_class": null,
    "item_type": "Primary Weapon",
    "description": "An hidden item, kind of weak but it could be just what you need against the right foe",
    "image": "",
    "level_required": 1,
    "damage": 50,
    "accuracy": 0.5,
    "defense": 0,
    "evasion": 0,
    "counter_attack": 0,
    "health_increase": 0,
    "lasts": 0,
    "stages": 0,
    "stage_damage_modifier": 0,
    "drop_scope": "NPC",
    "equip_scope": "Global",
    "pricing": [
      {
        "currency_name": "Bitcoin Testnet",
        "address": "2MvYjzw6qhCKGdS2Yt822W8YF9xM3kdtnjW",
        "amount": 50000000
      },
      {
        "currency_name": "Defcoin Mainnet",
        "address": "AFSz37wLo55572HBFQYnKWAoJRQco5SwrD",
        "amount": 5000000000
      },
      {
        "currency_name": "Bitcoin Mainnet",
        "address": "3PpajCEw5a9gfu31yZqwRTAbRxvXVmbMJd",
        "amount": 50000000
      }
    ]
  },
  {
    "id": 111,
    "name": "Dual Disc Launchers",
    "droid_class": null,
    "item_type": "Primary Weapon",
    "description": "Akimbo baby!",
    "image": "",
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
    "drop_scope": "NPC",
    "equip_scope": "Global",
    "pricing": [
      {
        "currency_name": "Bitcoin Testnet",
        "address": "2N5WWn2vwLHe29sF3rxzhVDxJ2N83kpZDdu",
        "amount": 269000000
      },
      {
        "currency_name": "Defcoin Mainnet",
        "address": "A4buy55xjGsEu7JhWxnW4thq8b7YrA98gW",
        "amount": 26900000000
      },
      {
        "currency_name": "Bitcoin Mainnet",
        "address": "33piSqVdyHiwEqG6E8x1a3RDcSh4zjKUwA",
        "amount": 269000000
      }
    ]
  },
  {
    "id": 104,
    "name": "Disc Launcher",
    "droid_class": null,
    "item_type": "Primary Weapon",
    "description": "Rapidly fires coins in a disc like manner.",
    "image": "",
    "level_required": 2,
    "damage": 10,
    "accuracy": 0.58,
    "defense": 0,
    "evasion": 0,
    "counter_attack": 0,
    "health_increase": 0,
    "lasts": 0,
    "stages": 0,
    "stage_damage_modifier": 0,
    "drop_scope": "NPC",
    "equip_scope": "Global",
    "pricing": [
      {
        "currency_name": "Bitcoin Testnet",
        "address": "2MzjG4sSQscSSXBjef8DT6wx8UuzhE75fVe",
        "amount": 253000000
      },
      {
        "currency_name": "Defcoin Mainnet",
        "address": "ACoDBVqY8dtFrt8eQSYRjQWfTgwjF8ZQfF",
        "amount": 25300000000
      },
      {
        "currency_name": "Bitcoin Mainnet",
        "address": "3EsbCXMMgedPzdktuzCEaesCRcnweSrPek",
        "amount": 253000000
      }
    ]
  }
]
```
