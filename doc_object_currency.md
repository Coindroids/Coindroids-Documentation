---
title: Currency
tags: [objects]
keywords: json, droid, object, patch, get
last_updated: December 23, 2015
summary: "Interacting with the avialable currencies through the REST API"

---

## Request

```HTTP
GET https://api.coindroids.com/currency
```

## Response Details

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


## Example

### Request

```HTTP
GET /currency HTTP/1.1
Host: api.coindroids.com:3000
Connection: close
User-Agent: YourBrowser
```

### Response header

```HTTP
HTTP/1.1 200 OK
transfer-encoding: chunked
Date: Sun, 22 Nov 2015 01:56:37 GMT
Server: postgrest/0.3.0.0
Content-Type: application/json
Content-Range: 0-0/1
Content-Location: /currency
```

### Response Body
```JSON
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
  },
  {
    "id": 2,
    "name": "Defcoin Mainnet",
    "starting_height": 625484,
    "netcode": "DFC",
    "min_attack_size": 10000,
    "max_attack_size": 314159265,
    "registration_fee": 10000,
    "satoshis_per_coin": 100000000,
    "transaction_fee_per_byte": 75,
    "max_payouts_per_settlement": 250,
    "min_change_amount": 1000000,
    "last_ingested": null,
    "largest_payout": null,
    "overall_purse_sum": 0,
    "total_number_of_attacks": 0,
    "total_amount_of_attacks": null,
    "total_number_of_item_purchases": 0,
    "total_droids": 2,
    "percentage_of_droids": 0.11764705882352941176
  },
  {
    "id": 3,
    "name": "Bitcoin Mainnet",
    "starting_height": 625484,
    "netcode": "BTC",
    "min_attack_size": 10000,
    "max_attack_size": 314159265,
    "registration_fee": 10000,
    "satoshis_per_coin": 100000000,
    "transaction_fee_per_byte": 75,
    "max_payouts_per_settlement": 250,
    "min_change_amount": 1000000,
    "last_ingested": null,
    "largest_payout": null,
    "overall_purse_sum": null,
    "total_number_of_attacks": 0,
    "total_amount_of_attacks": null,
    "total_number_of_item_purchases": 0,
    "total_droids": 0,
    "percentage_of_droids": 0.00000000000000000000
  }
]
```
