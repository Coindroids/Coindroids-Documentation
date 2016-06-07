## /payout

> Grab the 4 latest payouts

```javascript
// My Events (GET https://api.coindroids.com/payout)

jQuery.ajax({
    url: "https://api.coindroids.com/payout",
    type: "GET",
    data: {
        "order": "block_height.desc",
    },
    headers: {
        "Range": "0-10",
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
    # My Events
    # GET https://api.coindroids.com/payout

    try:
        response = requests.get(
            url="https://api.coindroids.com/payout",
            params={
                "order": "block_height.desc",
            },
            headers={
                "Range": "0-10",
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
curl -X "GET" "https://api.coindroids.com/payout?order=block_height.desc" \
	-H "Range: 0-10"

```


> Response Example

```
[
  {
    "currency": "Bitcoin Testnet",
    "block_height": 868029,
    "actions": [
      "Attack"
    ],
    "outcome_type": "Refund of overpayment",
    "amount": 0.00700000000000000000,
    "player": "Trunc",
    "droid": "Trunk"
  },
  {
    "currency": "Bitcoin Testnet",
    "block_height": 868029,
    "actions": [
      "Attack"
    ],
    "outcome_type": "Refund of overpayment",
    "amount": 0.00410000000000000000,
    "player": "Trunc",
    "droid": "Trunk"
  },
  {
    "currency": "Bitcoin Testnet",
    "block_height": 868029,
    "actions": [
      "Attack",
      "Attack"
    ],
    "outcome_type": "Droid destroyed",
    "amount": 0.07186051000000000000,
    "player": "Trogdor",
    "droid": "Trogdor1"
  },
  {
    "currency": "Bitcoin Testnet",
    "block_height": 868028,
    "actions": [
      "Attack",
      "Attack",
      "Attack"
    ],
    "outcome_type": "Droid destroyed",
    "amount": 0.0000000000000000000000000000,
    "player": "Trunc",
    "droid": "Rob1t"
  }
]
```

A list of all the payouts going out of the system. 

### Response 

|Name|Type|Description|
|---|---|---|
|currency|String|The name of the currency network the payout was sent on|
|block_height|Whole Number|The height of the block it was included in|
|actions|Action Type[]|The action type(s) that triggered the payout|
|outcome_type|Outcome Type[]|The outcome type(s) that triggered the payout|
|amount|Numeric|The amount sent out|
|player|String|The name of the player who received the payout (where applicable)|
|droid|String|The name of the Droid who received the payout (where applicable)|
 

