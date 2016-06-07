
## /currency

```javascript
// View specific currency (GET https://api.coindroids.com/currency)

jQuery.ajax({
    url: "https://api.coindroids.com/currency",
    type: "GET",
    data: {
        "netcode": "eq.BTC",
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
                "netcode": "eq.BTC",
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
curl -X "GET" "https://api.coindroids.com/currency?netcode=eq.BTC"
```

> The JSON returned will be formatted as: 

```
[
  {
    "id": 1,
    "name": "Bitcoin Testnet",
    "starting_height": 625484,
    "netcode": "XTN",
    "min_attack_size": 10000,
    "max_attack_size": 314159265,
    "registration_fee": 10000,
    "satoshis_per_coin": 100000000,
    "transaction_fee_per_byte": 75,
    "max_payouts_per_settlement": 250,
    "min_change_amount": 1000000,
    "last_ingested": {
      "block_id": 9006,
      "currency_id": 1,
      "block_hash": "000000008991c4654c715cd5aee7fdabe578e122750d588c411c0c8fb70789c8",
      "last_block_hash": "00000000a788ef252b103ebaf5de4ad6c4384cfa5537854ac8b2f38a37eb97ef",
      "height": 632282,
      "version": 4,
      "mined_time": "2016-01-09T10:26:34+00:00"
    },
    "largest_payout": 1249990000,
    "overall_purse_sum": 2446368,
    "total_number_of_attacks": 421,
    "total_amount_of_attacks": 3274158643,
    "total_number_of_item_purchases": 24,
    "total_droids": 15,
    "percentage_of_droids": 0.88235294117647058824
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
|last_ingested | Block&nbsp;(Condensed&nbsp;Object) | Block details about the last block ingested and processed into the system |
|largest_payout | Satoshi | The lagest payout sent out in the currency. Currently includes payouts returned due to voided actions (Unregistered play, Max attack amount, Item overage, etc )|
|overall_purse_sum| Satoshi | The amount currently found across all available purses |
|total_number_of_attacks| Whole Number | The total number of attacks taken place on this currency. Currently includes voided attacks|
|total_amonunt_of_attacks| Satoshi |  The total sum of transaction amounts sent as attacks on this currency. Currently includes voided attacks|
|total_number_of_item_purchases | Whole Number | The total number of item purchases actions taken place on this currency. Currently includes voided purchases|
|total_droids| Whole Number | Total total number of droids playing under this currency |
|percentage_of_droids| Numeric | The percantage of droids fighting under this currency compared to others |

