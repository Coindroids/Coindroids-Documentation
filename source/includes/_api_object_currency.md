
## /currency

```javascript
// View specific currency (GET https://api.coindroids.com/currency)

jQuery.ajax({
    url: "https://api.coindroids.com/currency",
    type: "GET",
    data: {
        "netcode": "eq.LTC",
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
    # View specific currency
    # GET https://api.coindroids.com/currency

    try:
        response = requests.get(
            url="https://api.coindroids.com/currency",
            params={
                "netcode": "eq.LTC",
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
curl -X "GET" "https://api.coindroids.com/currency?netcode=eq.LTC"
```

> The JSON returned will be formatted as: 

```
[
  {
    "id": 4,
    "name": "Litecoin Mainnet",
    "starting_height": 1173914,
    "netcode": "LTC",
    "min_attack_size": 100000,
    "max_attack_size": 314159265,
    "registration_fee": 1000000,
    "satoshis_per_coin": 100000000,
    "transaction_fee_per_byte": 350,
    "max_payouts_per_settlement": 1,
    "min_change_amount": 100000,
    "uri_scheme": "litecoin",
    "shield_cost": 1000000,
    "shield_address": "3BCZGwUBiWPSTXTC2XQP4eYBFTNh6sfrAS",
    "cover_cost": 1000000,
    "cover_address": "3Md51ftu445UpXxdEEyMR6daZ1GmbdTPGA",
    "token_size": 1000000,
    "last_ingested": {
      "block_id": 77697,
      "currency_id": 4,
      "block_hash": "25d35bbf3ab38761154502cc9c5bdf5f980af74e816bed92da71d01d779906a6",
      "last_block_hash": "e3d5c1abbf6b655888ca25f804ae6608f02d8c2536c389b34c10a25145ed46be",
      "height": 1181605,
      "version": 4,
      "mined_time": "2017-04-07T23:38:12+00:00"
    },
    "largest_payout": 198900000,
    "overall_purse_sum": 59596207,
    "total_number_of_attacks": 522,
    "total_amount_of_attacks": 858731000,
    "total_number_of_item_purchases": 49,
    "total_droids": 29,
    "percentage_of_droids": 0.67441860465116279070,
    "pending_payouts": 87
  }
]
```


This endpoint gives you full access to all the currency related data.


### Response Details

|Name             |Data Type     |Description            |
------------------|--------------|-----------------------|
|id               | Whole Number | The ID of the Currency|
|name             | String       | The science-given name of the Currency |
|netcode		  | String		 | A small call-sign used by the currency |
|min_attack_size  | Satoshi | The minimum number of satoshis required for an attack. Smaller amounts are considered donations. |
|max_attack_size  | Satoshi | The maximum number of satoshis that will be recognized as a valid attack. Larger attacks will be returned. |
|registration_fee | Satoshi | The number of satoshis required to register a droid under this currency |
|satoshis_per_coin| Satoshi | The amount of satoshis in one coin|
|transaction_fee_per_byte | Whole Number | The amount of fee added per byte of the transaction |
|max_payouts_per_settlement | Whole Number | The max number of settlement outputs allowed in each transaction |
|min_change_amonunt | Whole Number | The minimum number of satoshis added to a transaction as change |
|uri_scheme | String | Identifier used to initiate a URI for launching wallets|
|shield_cost | Satoshi | The cost of a Shield action in the currency |
|shield_address | Address | The address to send funds to to initiate the Shield action  |
|cover_cost | Sastoshi | The cost of the Cover action in the currency|
|cover_address | Address | The address to send funds to to initiate the Cover action  |
|last_ingested | Block&nbsp;(Condensed&nbsp;Object) | Block details about the last block ingested and processed into the system Inlcudes the following (last_ingested.*) |
|last_ingested.block_id | Whole Number | ID number of the last block processed |
|last_ingested.currency_id | Whole Number | ID of the currency... but.. you already know that so.. deprecated?|
|last_ingested.block_hash | String | The hash of the latest block processed|
|last_ingested.last_block_hash | String | The hash of the previous block processed |
|last_ingested.height | Whole Number | The height of the latest block processed |
|last_ingested.version | Whole Number | Block version code |
|last_ingested.mined_time | Timestamp | The actual time the block was mined |
|largest_payout | Satoshi | The lagest payout sent out in the currency. Currently includes payouts returned due to voided actions (Unregistered play, Max attack amount, Item overage, etc )|
|overall_purse_sum| Satoshi | The amount currently found across all available purses |
|total_number_of_attacks| Whole Number | The total number of attacks taken place on this currency. Currently includes voided attacks|
|total_amonunt_of_attacks| Satoshi |  The total sum of transaction amounts sent as attacks on this currency. Currently includes voided attacks|
|total_number_of_item_purchases | Whole Number | The total number of item purchases actions taken place on this currency. Currently includes voided purchases|
|total_droids| Whole Number | Total total number of droids playing under this currency |
|percentage_of_droids| Numeric | The percantage of droids fighting under this currency compared to others |
|pending_payouts| Whole Number| The total number of waiting payouts, including those that don't meet the payout threshold|
