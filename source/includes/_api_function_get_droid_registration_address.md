
## /rpc/get_droid_registration_address

```shell
curl -X "POST" "https://api.coindroids.com/rpc/get_droid_registration_address" \
	-H "Authorization: Bearer eyJhbGciOiJIUzI...2lXGhuBjtQ8Q" \
	-H "Content-Type: text/plain" \
	-d "{ \"droid_id\":YourDroidID }"
```

<aside class='warning'>
This RPC call requires that the request include the Authorization token
</aside>


This function is used to grab a new wallet sync address for a droid.

<aside class='notice'>
If you notice that the Coindroids universe is no longer recognizing your transactions, you likely need to call this function and use the address returned to re-sync your wallet. 
</aside>

