## /rpc/create_droid

```shell
curl -X "POST" "https://api.coindroids.com/rpc/create_droid" \
	-H "Authorization: Bearer eyJhbGciO...DSzsybGFgk" \
	-H "Content-Type: application/json" \
	-d "{\"name\":\"Droidy McDroidface\",\"currency_id\":\"1\",\"model\":\"Assault Training\"}"
```

```javascript
jQuery.ajax({
    url: "https://api.coindroids.com//rpc/create_droid",
    type: "POST",
    headers: {
        "Authorization": "Bearer eyJhbGc...sybGFgk",
        "Content-Type": "application/json",
    },
    contentType: "application/json",
    data: JSON.stringify({
        "name": "Droidy McDroidface",
        "model": "Assault Training",
        "currency_id": "1"
    })
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
import json


def send_request():
  try:
        response = requests.post(
            url="https://api.coindroids.com/rpc/create_droid",
            headers={
                "Authorization": "Bearer eyJhbGciOiJI...zsybGFgk",
                "Content-Type": "application/json",
            },
            data=json.dumps({
                "name": "Droidy McDroidface",
                "model": "Droidy McDroidface",
                "currency_id": "1"
            })
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')
```

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>


### Parameters

|Name | Type | Description|
|----|----|---|
|model| Model | See the list of models available for new droids below | 
|currency_id | Bigint | See the /currency endpoint for available currencies|
|name | CHARACTER VARYING| Your droids new classy moniker|

### Response Details

|Name | Description|
|----|----|
|droid| Droid Object |The droid object as if called through the /droid endpoint. Includines the following details (droid.*) |
|droid.id | Whole Number| The ID of the Droid|
|droid.name | String| The science-given name of the Droid |
|droid.currency_id | Whole Number | The ID of the currency realm the droid is in|
|droid.currency_code | Netcode | The three letter code for a currency (i.e. LTC)|
|droid.player_id | Whole Number | The ID of the droids squishy overlord | 
|droid.username | String | Name of the droids squishy overlord |
|droid.attack_address| Cryptocurrency Address | The address other players can use to attack this droid|
|droid.primary\_ammunition_clip| Cryptocurrency Address | The primary address used for payouts involving this droid |
|droid.additional\_ammunition_clips | Cryptocurrency Address[] | Additional addresses tracked for droid actions involving this droid|
|droid.level | Whole Number | The level of a droid |
|droid.experience | Whole Number | The total experience gained by this droid to date |
|droid.health_current | Whole Number | The current state of the health for a droid going into the next processing block|
|droid.health_max | Whole Number | The maximum health that this droid can have |
|droid.purse_current | Whole Number | The current state of the purse for a droid going into the next block processing|
|droid.is_npc | Boolean | _[True, False]_ Is this human controlled or a coindroids bot instance? |
|droid.is_active| Boolean | Has this droid been properly registered to a player wallet|
|droid.is_shielded | Boolean | Is the droid currently in a Shielding status? |
|droid.is_covered | Boolean | Is the droid currently in a Covered status? |
|droid.death_height | Whole Number | The height in which the droid died (NULL if not currently dead)|
|droid.is_dead| Boolean | Is the droid currently dead? |
|droid.last_attack | Whole Number | The height of the last Attack action performed by this droid|
|droid.created_at | Timestamp | The date and time of droid creation |
|droid.build | Items[] | A description of the items which make up the build of this droid |
|droid.build[].item_id | Whole Number | The ID of the item equipped in the build | 
|droid.build[].name | String | The name of the item equipped in the build|
|droid.build[].class | Class Type | The class of the item equipped in the build |
|droid.build[].image | File Path | The path to the static image hosted for the item|
|droid.build[].model | Model Type | The model of the item equipped in the build |
|droid.build[].details | Item Details Object | The full attributes of the item equipped in the build|
|droid.build[].item_type | Item Type | The type of the item equipped in the build |
|droid.build[].short_name | String | A short identifier of the equipped item|
|droid.build[].description | String | A long description of the equipped item |
|droid.build[].level_required | Whole Number| The level that must be met for the item to be equippable|
|droid.build[].real_item_type | String | Another Item Type field that made sense at the time but I don't quite recall why this is here|
|droid.attribute| Attributes | The culminating stats of a droid build. Includes the following details (attribute.*)|
|droid.attribute.ems | Numeric |Value between 0-100%, used when calculating EMI |
|droid.attribute.class | Class Type| The resulting Class of the droid build|
|droid.attribute.model | Model Type| The resulting Model of the droid build|
|droid.attribute.defense| Numeric| Value between 0-100%, used during attack calculations|
|droid.attribute.accuracy|Numeric| Value between 0-100%, used during attack calculations|
|droid.attribute.clip_size|Whole Number| The number of bullets (i.e. Tokens) that can be fired per block |
|droid.attribute.base_damage|Numeric|Value between 0-100%, used during attack calculations|
|droid.attribute.weapon_unlock|Numeric|Value between 0-100%, used during attack calculations|
|droid.attribute.accuracy_likely|Numeric|Value between 0-100%, the average accuracy to expect from the build|
|droid.attribute.blueprint|Droid Blueprint Object| An object that denotes each item and the position it occupies on the droid|
|droid.composition| Composition Objects|The makeup of the droids materials (composition.<item_id>.*)|
|droid.pending_build | Build Object | The full new build of a droid including build, composition, part_list and attribute|
|droid.currency_in | Satoshi | Total amount of value sent to the system from this droid |
|droid.currency_out | Satoshi | Total amount of payouts sent to this droid from the system |
|droid.highest_payout | Satoshi | Largest payout won by the droid (currently includes refunds from voided actions)|
|droid.attacks | Whole Number | Total number of attacks the droid has made |
|droid.targeted | Whole Number | Total number of attacks by other droids against this droid |
|droid.deaths| Whole Number | Total deaths this droid has experienced |
|droid.average_damage_performed| Whole Number | Average damage done by the droid in an attack |
|droid.total_damage_performed| Whole Number | Total damage performed by this droid across all attacks |
|droid.total_damage_defended| Whole Number | Total damage defended against by this droid across all attacks against it |
|droid.most_targeted_id| Whole Number | The target this droid attacks most often |
|droid.most_targeted_name | String | The name of the target this droid attacks most often |
|droid.worst_enemy_id| Whole Number | The droid that targets this droid the most |
|droid.worst_enemy_name | String | The name of the droid that targets this droid the most |
|errors| Error[] |An array of errors with the following attributes (errors[].*)|
|errors[].field| String| Error Label|
|errors[].message| String | Error descrption| 


### Potential Errors

| Field | Message |
|----|----|
|name| Droid name has illegal characters [0-9a-zA-Z\-_]{3,20}|
|name| Droid name is taken |
|currency_id|Player already has a droid under this currency|
|model|Base model unavailable to Player|
|unknown|An unknown error has occured|
|session|Player must be logged in to perform this action|
