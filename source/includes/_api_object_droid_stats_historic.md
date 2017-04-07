## /droid_stats_historic

```javascript
// Historic stats for Droids (GET https://api.coindroids.com/droid_stats_historic)

jQuery.ajax({
    url: "https://api.coindroids.com/droid_stats_historic",
    type: "GET",
    data: {
        "droid_id": "eq.4",
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
    # Historic stats for Droids
    # GET https://api.coindroids.com/droid_stats_historic

    try:
        response = requests.get(
            url="https://api.coindroids.com/droid_stats_historic",
            params={
                "droid_id": "eq.4",
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
curl "https://api.coindroids.com/droid_stats_historic?droid_id=eq.4&order=height.desc" \
     -H "Range: 0-2"
```

> The JSON returned will be formatted as: 

```
[
  {
    "height": 1116682,
    "droid_id": 4,
    "level": 7,
    "experience": 16,
    "health": 7,
    "purse": 171060,
    "currency_in": 7060000,
    "currency_out": 33939328,
    "highest_payout": 10857857,
    "attacks": 4,
    "deaths": 3,
    "average_damage_performed": 13.2500000000000000,
    "total_damage_performed": 53,
    "total_damage_defended": 469
  },
  {
    "height": 1116681,
    "droid_id": 4,
    "level": 7,
    "experience": 16,
    "health": 7,
    "purse": 171060,
    "currency_in": 7060000,
    "currency_out": 33939328,
    "highest_payout": 10857857,
    "attacks": 4,
    "deaths": 3,
    "average_damage_performed": 13.2500000000000000,
    "total_damage_performed": 53,
    "total_damage_defended": 469
  },
  {
    "height": 1116680,
    "droid_id": 4,
    "level": 7,
    "experience": 16,
    "health": 7,
    "purse": 171060,
    "currency_in": 7060000,
    "currency_out": 33939328,
    "highest_payout": 10857857,
    "attacks": 4,
    "deaths": 3,
    "average_damage_performed": 13.2500000000000000,
    "total_damage_performed": 53,
    "total_damage_defended": 469
  }
]
```

The heart of the Coindroids system, the /droid API endpoint. 





|Name|Data Type|Description|
---|---|---|
| player_id | Whole Number| The ID of the Droid|
| height | Whole Number | The height in which the stats were taken from |
| level | Whole Number | The level of a droid |
| experience | Whole Number | The total experience gained by this droid to date |
| health | Whole Number | The current state of the health for a droid going into the next processing block|
| purse | Whole Number | The current state of the purse for a droid going into the next block processing|
| currency_in | Satoshi | Total amount of value sent to the system from this droid |
| currency_out | Satoshi | Total amount of payouts sent to this droid from the system |
| highest_payout | Satoshi | Largest payout won by the droid (currently includes refunds from voided actions)|
| attacks | Whole Number | Total number of attacks the droid has made |
| deaths| Whole Number | Total deaths this droid has experienced |
| average_damage_performed| Whole Number | Average damage done by the droid in an attack |
| total_damage_performed| Whole Number | Total damage performed by this droid across all attacks |
| total_damage_defended| Whole Number | Total damage defended against by this droid across all attacks against it |
