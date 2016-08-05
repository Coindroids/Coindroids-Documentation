## /rpc/set_droid_build

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>

Your droid is an ever evolving beast and the Coindroids universe is no different. Ensure your droid is always built to impress (and annihilate) through the set_droid_build call. 

<aside class='notice'>
Builds are not updated immediately, they are validated and put into a pending state. Droid builds are applied during the Block Processing procedures.
</aside>

### Parameters

|Name | Type | Description|
|----|----|---|
|droid_id|Bigint| The ID of the droid being updated|
|build|JSONB||



### Response Details

|Name | Description|
|----|----|
|Droid| The droid object as if called through the /droid endpoint. |




