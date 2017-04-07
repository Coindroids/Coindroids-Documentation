## /rpc/set_droid_payout_address

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>

This function allows you to change the payout address used when sending funds awarded to your droid. The Coindroids system will follow many wallets for your droid, but payouts are always sent to this one address. 


### Parameters

|Name | Type | Description|
|----|----|---|
|droid_id|Bigint| The ID of the droid being updated|
|payout_address|Address|Must already be an address associated with your droid|



### Response Details

|Name | Description|
|----|----|
|Droid Response| The droid object as if called through the /droid endpoint. |




