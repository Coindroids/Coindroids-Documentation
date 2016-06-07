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
