## /rpc/verify_droid_build

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>

Your droid is an ever evolving beast and the Coindroids universe is no different. Ensure your droid is always built to impress (and annihilate) through the verify_droid_build call. 


<aside class='notice'>
You must use set_droid_build if you want the changes to commit 
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




