
## /currency_stats_historic

```javascript
// Historic stats on Currency (GET https://api.coindroids.com/currency_stats_historic)

jQuery.ajax({
    url: "https://api.coindroids.com/currency_stats_historic",
    type: "GET",
    data: {
        "currency_id": "eq.4",
        "order": "height.desc",
    },
    headers: {
        "Range": "0-2",
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
    # Historic stats on Currency
    # GET https://api.coindroids.com/currency_stats_historic

    try:
        response = requests.get(
            url="https://api.coindroids.com/currency_stats_historic",
            params={
                "currency_id": "eq.4",
                "order": "height.desc",
            },
            headers={
                "Range": "0-2",
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
curl "https://api.coindroids.com/currency_stats_historic?currency_id=eq.4&order=height.desc" \
     -H "Range: 0-2"
```

> The JSON returned will be formatted as: 

```
[
  {
    "currency_id": 4,
    "height": 1181553,
    "largest_payout": 198900000,
    "overall_purse_sum": 58721417,
    "total_number_of_attacks": 521,
    "total_amount_of_attacks": 857111000,
    "total_number_of_item_purchases": 49,
    "total_droids": 29,
    "percentage_of_droids": 0.67441860465116279070,
    "pending_payouts": 86
  },
  {
    "currency_id": 4,
    "height": 1181552,
    "largest_payout": 198900000,
    "overall_purse_sum": 58721417,
    "total_number_of_attacks": 521,
    "total_amount_of_attacks": 857111000,
    "total_number_of_item_purchases": 49,
    "total_droids": 29,
    "percentage_of_droids": 0.67441860465116279070,
    "pending_payouts": 86
  },
  {
    "currency_id": 4,
    "height": 1181551,
    "largest_payout": 198900000,
    "overall_purse_sum": 58721417,
    "total_number_of_attacks": 521,
    "total_amount_of_attacks": 857111000,
    "total_number_of_item_purchases": 49,
    "total_droids": 29,
    "percentage_of_droids": 0.67441860465116279070,
    "pending_payouts": 86
  }
]
```


This endpoint gives you full access to all the currency related data.


### Response Details

|Name             |Data Type     |Description            |
------------------|--------------|-----------------------|
|currency_id      | Whole Number | The ID of the Currency|
|height | Whole Number | The height the stats were taken from|
|largest_payout | Satoshi | The lagest payout sent out in the currency. Currently includes payouts returned due to voided actions (Unregistered play, Max attack amount, Item overage, etc )|
|overall_purse_sum| Satoshi | The amount currently found across all available purses |
|total_number_of_attacks| Whole Number | The total number of attacks taken place on this currency. Currently includes voided attacks|
|total_amonunt_of_attacks| Satoshi |  The total sum of transaction amounts sent as attacks on this currency. Currently includes voided attacks|
|total_number_of_item_purchases | Whole Number | The total number of item purchases actions taken place on this currency. Currently includes voided purchases|
|total_droids| Whole Number | Total total number of droids playing under this currency |
|percentage_of_droids| Numeric | The percantage of droids fighting under this currency compared to others |
|pending_payouts| Whole Number| The number of payouts waiting in the system, including those that don't need the payout threshold |
