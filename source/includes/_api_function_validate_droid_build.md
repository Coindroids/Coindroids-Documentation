## /rpc/validate_droid_build

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>

Your droid is an ever evolving beast and the Coindroids universe is no different. Ensure your droid is always built to impress (and annihilate) through the validate_droid_build call. 


<aside class='notice'>
You must use set_droid_build if you want the changes to commit 
</aside>

### Parameters

|Name | Type | Description|
|----|----|---|
|droid_id|Whole Number| The ID of the droid being updated|
|build|JSONB||



### Response Details

|Name | Type | Description|
|----|---|---|
|build| Items[] | The build of a droid, as if accessed from the /droid endpoint. Includes the following details (build[].*) |
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
|part_list| Whole Number[]| Array of items involved in the droid build|
|composition| Composition Objects|The makeup of the droids materials (composition.<item_id>.*)|

