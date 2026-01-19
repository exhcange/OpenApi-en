# Coingecko docking

### Coin quotes

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/coinGecko/pub/v1/ticker`

**Request parameters**

no

**Response parameters**

| Name             | type   | Example                | description                                                               |
| ---------------- | ------ | ---------------------- | ------------------------------------------------------------------------- |
| ticker\_id       | string | BTC\_USDT              | token pair                                                                |
| base\_currency   | string | BTC                    | base currency                                                             |
| target\_currency | string | USDT                   | currency of account                                                       |
| last\_price      | number | 98000.0000000000000000 | last traded price of the base currency based on the given target currency |
| base\_volume     | number | 1.1200                 | 24-hour single side volume of the pair (in base units)                    |
| target\_volume   | number | 99000.0000000000       | 24-hour single side volume of the pair (denominated currency units)       |
| bid              | number | 97000                  | Current highest buy price                                                 |
| ask              | number | 98000                  | Current high and low order price                                          |
| high             | number | 98000                  | Rolling 24-hour highest trading price                                     |
| low              | number | 98000                  | Rolling 24-hour lowest trading price                                      |

**Sample response**

{% tabs %}
{% tab title="200" %}
```json
{
    "ETH_USDT": {
        "ticker_id": "ETH_USDT",
        "base_currency": "ETH",
        "target_currency": "USDT",
        "last_price": 238.2000000000000000,
        "base_volume": 0.0000,
        "target_volume": 0.000000,
        "bid": 0,
        "ask": 0,
        "high": 238.2,
        "low": 238.2
    },
    "BCH_USDT": {
        "ticker_id": "BCH_USDT",
        "base_currency": "BCH",
        "target_currency": "USDT",
        "last_price": 1.0000000000000000,
        "base_volume": 0.000000,
        "target_volume": 0E-10,
        "bid": 0,
        "ask": 0,
        "high": 1,
        "low": 1
    }
}
```
{% endtab %}
{% endtabs %}

### Disc data

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/coinGecko/pub/v1/orderbook`

**Request parameters**

| Name       | Type           | Description |
| ---------- | -------------- | ----------- |
| ticker\_id | string         | token pair  |
| depth      | integer(int32) | Order depth |

**Response parameters**

| Name       | type           | Example                     | description                                                              |
| ---------- | -------------- | --------------------------- | ------------------------------------------------------------------------ |
| ticker\_id | string         | BTC\_USDT                   | token pair                                                               |
| timestamp  | integer(int64) | 1766976278000               | Unix timestamp, in milliseconds, of the last update                      |
| bids       | array          | \[\[1000,0.1], \[2000,0.2]] | An array with two elements, the bid and quantity for each purchase       |
| asks       | array          | \[\[2000,0.2], \[3000,0.3]] | An array of two elements with the price and quantity for each sell order |

**Sample response**

{% tabs %}
{% tab title="200" %}
```json
{
    "ticker_id": "BTC_USDT",
    "timestamp": 1766976278000,
    "bids": [
        [
            98000,
            0.46938777
        ],
        [
            98500.93,
            0.1
        ]
    ],
    "asks": [
        [
            98000,
            0.46938777
        ],
        [
            98500.93,
            0.1
        ]
    ]
}
```
{% endtab %}
{% endtabs %}

### contracts

<mark style="color:blue;">`GET`</mark>` ``https://futuresopenapi.xxx.xx/pub/coingecko/contracts`&#x20;

**Request parameters**

| Name       | Type   | Description                                |
| ---------- | ------ | ------------------------------------------ |
| ticker\_id | string | contract\_name【Optional】, eg. "E-BTC-USDT" |

**Response parameters**

<table data-header-hidden><thead><tr><th valign="top">Name</th><th>Type</th><th>Example</th><th>Description</th></tr></thead><tbody><tr><td valign="top"><strong>Name</strong></td><td><strong>Type</strong></td><td><strong>Example</strong></td><td><strong>Description</strong></td></tr><tr><td valign="top">ticker_id</td><td>string</td><td>E-BTC-USDT</td><td>Identifier of a ticker with delimiter to separate base/target, eg. BTC-PERP</td></tr><tr><td valign="top">base_currency</td><td>string</td><td>BTC</td><td>Symbol/currency code of base pair, eg. BTC</td></tr><tr><td valign="top">target_currency</td><td>string</td><td>USDT</td><td>Symbol/currency code of target pair, eg. ETH</td></tr><tr><td valign="top">last_price</td><td>decimal</td><td>92000.36</td><td>Last transacted price of base currency based on given target currency</td></tr><tr><td valign="top">base_volume</td><td>decimal</td><td>0.2</td><td>24 hour trading single sided volume in base pair volume</td></tr><tr><td valign="top">target_volume</td><td>decimal</td><td>0.2</td><td>24 hour trading single sided volume in target pair volume</td></tr><tr><td valign="top">bid</td><td>decimal</td><td>92000.36</td><td>Current highest bid price</td></tr><tr><td valign="top">ask</td><td>decimal</td><td>92000.36</td><td>Current lowest ask price</td></tr><tr><td valign="top">high</td><td>decimal</td><td>92100.36</td><td>Rolling 24-hours highest transaction price</td></tr><tr><td valign="top">low</td><td>decimal</td><td>91900.36</td><td>Rolling 24-hours lowest transaction price</td></tr><tr><td valign="top">product_type</td><td>string</td><td>Perpetual</td><td>What product is this? Futures, Perpetual, Options?</td></tr><tr><td valign="top">open_interest</td><td>decimal</td><td>1116.3655</td><td>The open interest in the last 24 hours in contracts (in base currency)</td></tr><tr><td valign="top">open_interest_usd</td><td>decimal</td><td>102573030.064</td><td>The open interest in the last 24 hours in contracts (in USD)</td></tr><tr><td valign="top">index_price</td><td>decimal</td><td>92100.36</td><td>Underlying index price</td></tr><tr><td valign="top">index_name</td><td>string</td><td>BTC-USDT</td><td>Name of the underlying index if any</td></tr><tr><td valign="top">index_currency</td><td>string</td><td>BTC</td><td>Underlying currency for index</td></tr><tr><td valign="top">start_timestamp</td><td>integer</td><td>0</td><td>Starting of this derivative product (relevant for expirable futures or options)</td></tr><tr><td valign="top">end_timestamp</td><td>integer</td><td>0</td><td>Ending of this derivative product (relevant for expirable futures or options)</td></tr><tr><td valign="top">funding_rate</td><td>decimal</td><td>0</td><td>Current funding rate</td></tr><tr><td valign="top">next_funding_rate</td><td>decimal</td><td>0</td><td>Upcoming predicted funding rate</td></tr><tr><td valign="top">next_funding_rate_timestamp</td><td>integer</td><td>1768291200000</td><td>Timestamp of the next funding rate change</td></tr><tr><td valign="top">contract_type</td><td>string</td><td>Vanilla</td><td>Describes the type of contract - Vanilla, Inverse or Quanto?</td></tr><tr><td valign="top">contract_price_currency</td><td>string</td><td>USDT</td><td>Describes the currency which the contract is priced in.</td></tr><tr><td valign="top">contract_price</td><td>decimal</td><td>92100.36</td><td>Describes the price per contract. (If not same as last price)</td></tr><tr><td valign="top">timestamp</td><td>integer</td><td>1768289995029</td><td>query data timestamp</td></tr></tbody></table>

**Sample request**

```
https://futuresopenapi.xxx.xx/pub/coingecko/contracts?ticker_id=E-BTC-USDT
```

**Sample response**

```json
{
    "code": "0",
    "msg": "success",
    "data": {
        "contracts": [
            {
                "ticker_id": "E-BTC-USDT",
                "base_currency": "BTC",
                "target_currency": "USDT",
                "last_price": 0,
                "base_volume": 0,
                "target_volume": 0,
                "bid": null,
                "ask": 9.8E+4,
                "high": 0,
                "low": 0,
                "product_type": "Perpetual",
                "open_interest": 1116.3655,
                "open_interest_usd": 102573030.06495740245,
                "index_price": 0,
                "index_name": "BTC-USDT",
                "index_currency": "BTC",
                "start_timestamp": 0,
                "end_timestamp": 0,
                "funding_rate": 0,
                "next_funding_rate": 0,
                "next_funding_rate_timestamp": 1768291200000,
                "contract_type": "Vanilla",
                "contract_price_currency": "USDT",
                "contract_price": 0,
                "timestamp": 1768289995029
            },
            {
                "ticker_id": "E-ETH-USDT",
                "base_currency": "ETH",
                "target_currency": "USDT",
                "last_price": 0,
                "base_volume": 0,
                "target_volume": 0,
                "bid": null,
                "ask": null,
                "high": 0,
                "low": 0,
                "product_type": "Perpetual",
                "open_interest": 3004.17,
                "open_interest_usd": 9383427.795980901,
                "index_price": 0,
                "index_name": "ETH-USDT",
                "index_currency": "ETH",
                "start_timestamp": 0,
                "end_timestamp": 0,
                "funding_rate": 0,
                "next_funding_rate": 0,
                "next_funding_rate_timestamp": 1768291200000,
                "contract_type": "Vanilla",
                "contract_price_currency": "USDT",
                "contract_price": 0,
                "timestamp": 1768289995029
            }
        ]
    }
}

```

### contract-orderbook

<mark style="color:blue;">`GET`</mark>` ``https://futuresopenapi.xxx.xx/pub/coingecko/orderbook`&#x20;

**Request parameters**

| Name       | Type           | Description                     |
| ---------- | -------------- | ------------------------------- |
| ticker\_id | string         | contract\_name, e. "E-BTC-USDT" |
| depth      | integer(int32) | Order depth                     |

**Response parameters**

| **Name**   | **Type**    | **Example**                                            | **Description**                                                                 |
| ---------- | ----------- | ------------------------------------------------------ | ------------------------------------------------------------------------------- |
| ticker\_id | string      |   E-BTC-USDT                                           | A pair such as "BTC-PERP", with delimiter between different cryptoassets        |
| timestamp  |   timestamp |   1768289995029                                        | Unix timestamp in milliseconds for when the last updated time occurred.         |
| bids       |   decimal   | <p>[<br>[98000,0.469387],<br>[98500.93,0.1]<br>]</p>   | An array containing 2 elements. The offer price and quantity for each bid order |
| asks       |   decimal   | <p>[<br>[97000,0.46938777],<br>[96500.93,0.1]<br>]</p> | An array containing 2 elements. The ask price and quantity for each ask order   |

**Sample request**

```
https://futuresopenapi.xxx.xx/pub/coingecko/orderbook?ticker_id=E-BTC-USDT&dept=100
```

**Sample response**

```json
{
    "code": "0",
    "msg": "success",
    "data": {
        "orderbook": {
            "ticker_id": "E-BTC-USDT",
            "asks": [
                [
                    98000,
                    0.46938777
                ],
                [
                    98500.93,
                    0.1
                ],
                [
                    100000,
                    3
                ],
                [
                    1800000,
                    1.111
                ],
                [
                    2000000,
                    1
                ]
            ],
            "bids": [
                [
                    97000,
                    0.46938777
                ],
                [
                    96500.93,
                    0.1
                ],
                [
                    96000,
                    3
                ],
                [
                    95500,
                    1.111
                ],
                [
                    95000,
                    1
                ]
            ],
            "timestamp": 1768289995029
        },
        "ticker_id": "E-BTC-USDT"
    }
}
```



