# Contract

## Public

### Security: [None](broken-reference)

Endpoints under **Public** section can be accessed freely without requiring any API-key or signatures

{% swagger baseUrl="https://futuresopenapi.xxx.com" path="/fapi/v1/ping" method="get" summary=" Test Connectivity" %}
{% swagger-description %}
 This endpoint checks connectivity to the host
{% endswagger-description %}

{% swagger-response status="200" description="" %}
```
{}
```
{% endswagger-response %}
{% endswagger %}



{% swagger baseUrl="https://futuresopenapi.xxx.com" path="/fapi/v1/time" method="get" summary="Check Server Time" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```
{
    "serverTime":1607702400000,
    "timezone":Chinese standard time
}
```
{% endswagger-response %}
{% endswagger %}

#### Response:

| name       | type   | example             | description      |
| ---------- | ------ | ------------------- | ---------------- |
| serverTime | long   | 1607702400000       | server timestamp |
| timezone   | string | China standard time | server time zone |

{% swagger baseUrl="https://futuresopenapi.xxx.com /fapi/v1/contracts" path="" method="get" summary="Contract List" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200" description="" %}
```
[
    {
        "symbol": "H-HT-USDT",
        "pricePrecision": 8,
        "side": 1,
        "maxMarketVolume": 100000,
        "multiplier": 6,
        "minOrderVolume": 1,
        "maxMarketMoney": 10000000,
        "type": "H",
        "maxLimitVolume": 1000000,
        "maxValidOrder": 20,
        "multiplierCoin": "HT",
        "minOrderMoney": 0.001,
        "maxLimitMoney": 1000000,
        "status": 1
    }
]
```
{% endswagger-response %}
{% endswagger %}

#### Response: <a href="#response-1" id="response-1"></a>

| name            | type   | example      | description                                                                       |
| --------------- | ------ | ------------ | --------------------------------------------------------------------------------- |
| symbol          | string | `E-BTC-USDT` | Contract name                                                                     |
| status          | number | `1`          | status（0：cannot trade，1：can trade                                                 |
| type            | string | `S`          | contract type, E: perpetual contract, S: test contract, others are mixed contract |
| side            | number | `1`          | Contract direction(backwards：0，1：forward)                                         |
| multiplier      | number | `0.5`        | Contract face value                                                               |
| multiplierCoin  | string | `BTC`        | Contract face value unit                                                          |
| pricePrecision  | number | `4`          | Precision of the price                                                            |
| minOrderVolume  | number | `10`         | Minimum order volume                                                              |
| minOrderMoney   | number | `10`         | Minimum order value                                                               |
| maxMarketVolume | number | `100000`     | Market price order maximum volume                                                 |
| maxMarketMoney  | number | `100000`     | Market price order maximum value                                                  |
| maxLimitVolume  | number | `100000`     | Limit price order maximum volume                                                  |
| maxValidOrder   | number | `100000`     | Maximum valid order quantity                                                      |

## Market <a href="#hang-qing-xiang-guan" id="hang-qing-xiang-guan"></a>

### Security: [None](https://exdocs.gitbook.io/v/general-info#jie-kou-jian-quan-lei-xing)​ <a href="#an-quan-lei-xing-none-1" id="an-quan-lei-xing-none-1"></a>

Market section can be accessed freely without requiring any API-key or signatures.

{% swagger baseUrl="https://futuresopenapi.xxx.com /fapi/v1/depth" path="" method="get" summary="Depth" %}
{% swagger-description %}
Market depth data  
{% endswagger-description %}

{% swagger-parameter in="query" name="limit" type="integer" %}
Default 100, Max 100
{% endswagger-parameter %}

{% swagger-parameter in="query" name="Contract name" type="string" %}
Contract Name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-response status="200" description="Successfully retrieve market depth data" %}
```java
{
  "bids": [
    [
      "3.90000000",   // price
      "431.00000000"  // quantity
    ],
    [
      "4.00000000",
      "431.00000000"
    ]
  ],
  "asks": [
    [
      "4.00000200",  // price
      "12.00000000"  // quantity
    ],
    [
      "5.10000000",
      "28.00000000"
    ]
  ]
}
```
{% endswagger-response %}
{% endswagger %}



#### Response: <a href="#response-2" id="response-2"></a>

| name | type | example         | description              |
| ---- | ---- | --------------- | ------------------------ |
| time | long | `1595563624731` | Current Timestamp  (ms)  |
| bids | list | Look below      | Order book purchase info |
| asks | list | Look below      | Order book selling info  |

The fields bids and asks are lists of order book price level entries, sorted from best to worst.

| name | type  | example | description                               |
| ---- | ----- | ------- | ----------------------------------------- |
| ' '  | float | `131.1` | price level                               |
| ' '  | float | `2.3`   | Total order quantity for this price level |

{% swagger baseUrl="https://futuersopenapi.xxx.com /fapi/v1/ticker" path="" method="get" summary="24hrs ticker" %}
{% swagger-description %}
24 hour price change statistics
{% endswagger-description %}

{% swagger-parameter in="query" name="Contract name" type="string" %}
Contract  name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-response status="200" description="Successfully obtain ticker info" %}
```java
{
    "high": "9279.0301",
    "vol": "1302",
    "last": "9200",
    "low": "9279.0301",
    "rose": "0",
    "time": 1595563624731
}
```
{% endswagger-response %}
{% endswagger %}

#### Response:

| name | type   | example         | description     |
| ---- | ------ | --------------- | --------------- |
| time | long   | `1595563624731` | Open time       |
| high | float  | `9900`          | Higher price    |
| low  | float  | `8800.34`       | Lower price     |
| last | float  | `8900`          | Newest price    |
| vol  | float  | `4999`          | Trade volume    |
| rose | string | +0.5            | Price variation |

{% swagger baseUrl="https://futuersopenapi.xxx.com /fapi/v1/index" path="" method="get" summary="Get index/marked price" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="Contract name" type="string" %}
Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="string" %}
Default 100, Max 100
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```java
{
    "markPrice": 581.5,
    "indexPrice": 646.3933333333333,
    "lastFundingRate": 0.001,
    "contractName": "E-ETH-USDT",
    "time": 1608273554063
}
```
{% endswagger-response %}
{% endswagger %}

#### **Response:**

| name              | type   | example      | Description       |
| ----------------- | ------ | ------------ | ----------------- |
| `indexPrice`      | float  | `0.055`      | Index price       |
| `markPrice`       | float  | `0.0578`     | Marked price      |
| `contractName`    | string | `E-BTC-USDT` | Contract name     |
| `lastFundingRate` | float  | `0.123`      | Current fund rate |

{% swagger baseUrl="https://futuresopenapi.xxx.com /fapi/v1/klines" path="" method="get" summary="Kline/charts data" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="ContractName" type="string" %}
Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="query" name="interval" type="string" %}
K-line interval, identifies the sent value as: 

`1min`

,

`5min`

,

`15min`

,

`30min`

,

`1h`

,

`1day`

,

`1week`

,

`1month`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="integer" %}
Default 100, Max 300
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```java
[
    {
        "high": "6228.77",
        "vol": "111",
        "low": "6228.77",
        "idx": 1594640340,
        "close": "6228.77",
        "open": "6228.77"
    },
    {
        "high": "6228.77",
        "vol": "222",
        "low": "6228.77",
        "idx": 1587632160,
        "close": "6228.77",
        "open": "6228.77"
    },
    {
        "high": "6228.77",
        "vol": "333",
        "low": "6228.77",
        "idx": 1587632100,
        "close": "6228.77",
        "open": "6228.77"
    }
]
```
{% endswagger-response %}
{% endswagger %}

#### **Response:**

| name    | type  | example         | description          |
| ------- | ----- | --------------- | -------------------- |
| `idx`   | long  | `1538728740000` | Start timestamp (ms） |
| `open`  | float | `36.00000`      | Open price           |
| `close` | float | `33.00000`      | Closing price        |
| `high`  | float | `36.00000`      | Max price            |
| `low`   | float | `30.00000`      | Min price            |
| `vol`   | float | `2456.111`      | Trade volume         |

## Trading <a href="#jiao-yi-xiang-guan" id="jiao-yi-xiang-guan"></a>

### Security: [TRADE](https://exdocs.gitbook.io/v/general-info#jie-kou-jian-quan-lei-xing)​ <a href="#an-quan-lei-xing-trade" id="an-quan-lei-xing-trade"></a>

&#x20;All interfaces under the transaction require [signature and API-key verification​](https://exdocs.gitbook.io/v/v/english/general-info#signed-trade-yu-userdata-endpoint-security)

{% swagger baseUrl="https://futuresopenapi.xxx.com /fapi/v1/order" path="" method="post" summary="Order creation" %}
{% swagger-description %}
Creation of single new orders
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
Time stamp
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Signature
{% endswagger-parameter %}

{% swagger-parameter in="body" name="volume" type="number" %}
Order quantity
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="number" %}
Order price
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractName" type="string" %}
Contract name E.g. 

`E-BTC-USDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
Order type, 

`LIMIT/MARKET`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="side" type="string" %}
trade direction, 

`BUY/SELL`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="open" type="string" %}
Open balancing direction, 

`OPEN/CLOSE`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="positionType" type="number" %}
Hold-up position, 

`1 full position, 2 restrictive position`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="clientOrderId" type="string" %}
Client order identity, a string with length less than 32 bit
{% endswagger-parameter %}

{% swagger-parameter in="body" name="timeInForce" type="string" %}
`IOC, FOK, POST_ONLY`
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```java
{
    "orderId": 256609229205684228
}
```
{% endswagger-response %}
{% endswagger %}

#### Response:

| name    | type   | example              | description |
| ------- | ------ | -------------------- | ----------- |
| orderId | String | `256609229205684228` | Order ID    |

{% swagger method="post" path="" baseUrl="https://futuresopenapi.xxx.com /fapi/v1/conditionOrder" summary="Condition order creation" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
Time stamp
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Signature
{% endswagger-parameter %}

{% swagger-parameter in="body" name="volume" type="number" %}
Order quantity
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="number" %}
Order price
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractName" type="string" %}
Contract name E.g. 

`E-BTC-USDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" type="string" %}
Order type, 

`LIMIT/MARKET`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="side" type="string" %}
trade direction, 

`BUY/SELL`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="open" type="string" %}
Open balancing direction, 

`OPEN/CLOSE`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="positionType" type="number" %}
Hold-up position, 

`1 full position, 2 restrictive position`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="triggerPrice" type="string" %}
trigger price
{% endswagger-parameter %}

{% swagger-parameter in="body" name="triggerType" type="string" %}
trigger type 

`3UP/4DOWN`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
     "orderId": 256609229205684228
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://futuresopenapi.xxx.com /fapi/v1/cancel" path="" method="post" summary="Cancel order" %}
{% swagger-description %}
Speed limit rules: 20 times/ 2 seconds
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="integer" %}
Time stamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractName" type="string" %}
Contract name E.g. 

`E-BTC-USDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="orderId" type="string" %}
Order ID
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```java
{
    "orderId": 256609229205684228
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://futuresopenapi.xxx.com /fapi/v1/order" path="" method="get" summary="Order details" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="contractName" type="string" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
[
    {
       "side": "BUY",
       "executedQty": 0,
       "orderId": 259396989397942275,
       "price": 10000.0000000000000000,
       "origQty": 1.0000000000000000,
       "avgPrice": 0E-8,
       "transactTime": "1607702400000",
       "action": "OPEN",
       "contractName": "E-BTC-USDT",
       "type": "LIMIT",
       "status": "INIT"
    }
]


```
{% endswagger-response %}
{% endswagger %}

#### Response:

| name           | type   | example              | description                                                                                                                                                                           |
| -------------- | ------ | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `orderId`      | long   | `150695552109032492` | Order ID（system generated                                                                                                                                                             |
| `contractName` | string | `E-BTC-USDT`         | Contract name                                                                                                                                                                         |
| `price`        | float  | `10.5`               | Order price                                                                                                                                                                           |
| `origQty`      | float  | `10.5`               | Order quantity                                                                                                                                                                        |
| `executedQty`  | float  | `20`                 | Order quantity                                                                                                                                                                        |
| `avgPrice`     | float  | `10.5`               | Average transaction price                                                                                                                                                             |
| `symbol`       | string | `BHTUSDT`            | Coin pair name                                                                                                                                                                        |
| `status`       | string | `NEW`                | Order status. Possible values are：`NEW`(new order，not filled)、`PARTIALLY_FILLED`（partially filled）、`FILLED`（fully filled）、`CANCELLED`（already cancelled）and`REJECTED`（order rejected） |
| `side`         | string | `NEW`                | Order direction. Possible values can only be：BUY（buy long）and SELL（sell short）                                                                                                        |
| `action`       | string | `OPEN`               | `OPEN/CLOSE`                                                                                                                                                                          |
| `transactTime` | long   | `1607702400000`      | Order creation time                                                                                                                                                                   |

{% swagger baseUrl="https://futuresopenapi.xxx.com /fapi/v1/openOrders" path="" method="get" summary="Open order" %}
{% swagger-description %}
**Speed limit rules:**

\


**Obtain open contract, the user's current order**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="integer" %}
time stamp
{% endswagger-parameter %}

{% swagger-parameter in="query" name="contractName" type="string" %}
Contract name 

`E-BTC-USDT`
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```java
[
    {
       "side": "BUY",
       "executedQty": 0,
       "orderId": 259396989397942275,
       "price": 10000.0000000000000000,
       "origQty": 1.0000000000000000,
       "avgPrice": 0E-8,
       "transactTime": "1607702400000",
       "action": "OPEN",
       "contractName": "E-BTC-USDT",
       "type": "LIMIT",
       "status": "INIT"
    }
]

```
{% endswagger-response %}
{% endswagger %}

#### **Response:**

| name           | type   | example              | description                                                                                                                                                                           |
| -------------- | ------ | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `orderId`      | long   | `150695552109032492` | Order ID（system generated）                                                                                                                                                            |
| `contractName` | string | `E-BTC-USDT`         | Contract name                                                                                                                                                                         |
| `price`        | float  | `4765.29`            | Order price                                                                                                                                                                           |
| `origQty`      | float  | `1.01`               | Order quantity                                                                                                                                                                        |
| `executedQty`  | float  | `1.01`               | Filled orders quantity                                                                                                                                                                |
| `avgPrice`     | float  | `4754.24`            | Filled orders average price                                                                                                                                                           |
| `type`         | string | `LIMIT`              | Order type. Possible values can only be:`LIMIT`(limit price) and`MARKET`（market price）                                                                                                |
| `side`         | string | `BUY`                | Order direction. Possible values can only be：`BUY`（buy long）and `SELL`（sell short）                                                                                                    |
| `status`       | string | `NEW`                | Order status. Possible values are：`NEW`(new order，not filled)、`PARTIALLY_FILLED`（partially filled）、`FILLED`（fully filled）、`CANCELLED`（already cancelled）and`REJECTED`（order rejected） |
| `action`       | string | `OPEN`               | `OPEN/CLOSE`                                                                                                                                                                          |
| `transactTime` | long   | `1607702400000`      | Order creation time,                                                                                                                                                                  |

{% swagger method="post" path="/fapi/v1/orderHistorical" baseUrl="https://futuresopenapi.xxx.com" summary="order history" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
time stamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractName" type="string" %}
Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="limit" type="string" %}
Lines per page, default 100, max 1000
{% endswagger-parameter %}

{% swagger-parameter in="body" name="fromId" type="long" %}
Start retrieving from this Id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
        "side":"BUY",
        "clientId":"0",
        "ctimeMs":1632903411000,
        "positionType":2,
        "orderId":777293886968070157,
        "avgPrice":41000,
        "openOrClose":"OPEN",
        "leverageLevel":26,
        "type":4,
        "closeTakerFeeRate":0.00065,
        "volume":2,
        "openMakerFeeRate":0.00025,
        "dealVolume":1,
        "price":41000,
        "closeMakerFeeRate":0.00025,
        "contractId":1,
        "ctime":"2021-09-29T16:16:51",
        "contractName":"E-BTC-USDT",
        "openTakerFeeRate":0.00065,
        "dealMoney":4.1,
        "status":4
    }
]
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="fapi/v1/profitHistorical" baseUrl="https://futuresopenapi.xxx.com/" summary="profit history" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
time stamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="contractName" type="string" %}
Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="body" name="limit" type="string" %}
Lines per page, default 100, max 1000
{% endswagger-parameter %}

{% swagger-parameter in="body" name="fromId" type="long" %}
Start retrieving from this Id
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
        "side":"SELL",
        "positionType":2,
        "tradeFee":-5.23575,
        "realizedAmount":0,
        "leverageLevel":26,
        "openPrice":44500,
        "settleProfit":0,
        "mtime":1632882739000,
        "shareAmount":0,
        "openEndPrice":44500,
        "closeProfit":-45,
        "volume":900,
        "contractId":1,
        "historyRealizedAmount":-50.23575,
        "ctime":1632882691000,
        "id":8764,
        "capitalFee":0
    }
]
```
{% endswagger-response %}
{% endswagger %}



{% swagger baseUrl="https://futuresopenapi.xxx.com /fapi/v1/myTrades" path="" method="get" summary="Order record" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="string" %}
time stamp
{% endswagger-parameter %}

{% swagger-parameter in="query" name="contractName" type="string" %}
Contract name E.g. E-BTC-USDT
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="string" %}
Lines per page, default 100, max 1000
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fromId" type="long" %}
Start retrieving from this tradeId
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```java
[
  {
    "symbol": "ETHBTC",
    "id": 100211,
    "bidId": 150695552109032492,
    "askId": 150695552109032493,
    "price": "4.00000100",
    "qty": "12.00000000",
    "time": 1499865549590,
    "isBuyer": true,
    "isMaker": false,
    "fee":"0.001"
  },...
]
```
{% endswagger-response %}
{% endswagger %}

#### **Response:** <a href="#response-9" id="response-9"></a>

| name         | type    | example            | description                                         |
| ------------ | ------- | ------------------ | --------------------------------------------------- |
| symbol       | string  | ETHBTC             | Coin name(trade pair)                               |
| tradeId      | number  | 28457              | Trade ID                                            |
| bidId        | long    | 150695552109032492 | Buyer order ID                                      |
| askId        | long    | 150695552109032493 | Seller order ID                                     |
| bidUserId    | integer | 10024              | Buyer user ID                                       |
| askUserId    | integer | 10025              | Seller user ID                                      |
| price        | float   | 4.01               | Filled price                                        |
| qty          | float   | 12                 | Trade quantity                                      |
| amount       | float   | 5.38               | Filled amount                                       |
| time         | number  | 1499865549590      | Trade time stamp                                    |
| fee          | number  | 0.001              | Trading fees                                        |
| side         | string  | buy                | Current order direction BUY purchase, SELL  selling |
| contractName | string  | E-BTC-USDT         | Contract name                                       |
| isMaker      | boolean | true               | is it maker?                                        |
| isBuyer      | boolean | true               | is it buyer?                                        |

## Account <a href="#zhang-hu" id="zhang-hu"></a>

### Security: [USER\_DATA](https://exdocs.gitbook.io/v/general-info#jie-kou-jian-quan-lei-xing)​ <a href="#an-quan-lei-xing-userdata" id="an-quan-lei-xing-userdata"></a>

All interfaces under the account require [signature and API-key verification​](https://exdocs.gitbook.io/v/v/english/general-info#signed-trade-yu-userdata-endpoint-security)

{% swagger baseUrl="https://futuresopenapi.xxx.com /fapi/v1/account" path="" method="get" summary="Account info" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" type="string" %}
Signature
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" type="integer" %}
time stamp
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```java
{
    "account": [
        {
            "marginCoin": "USDT",
            "accountNormal": 999.5606,
            "accountLock": 23799.5017,
            "partPositionNormal": 9110.7294,
            "totalPositionNormal": 0,
            "achievedAmount": 4156.5072,
            "unrealizedAmount": 650.6385,
            "totalMarginRate": 0,
            "totalEquity": 99964804.560,
            "partEquity": 13917.8753,
            "totalCost": 0,
            "sumMarginRate": 873.4608,
            "positionVos": [
                {
                    "contractId": 1,
                    "contractName": "E-BTC-USDT",
                    "contractSymbol": "BTC-USDT",
                    "positions": [
                        {
                            "id": 13603,
                            "uid": 10023,
                            "contractId": 1,
                            "positionType": 2,
                            "side": "BUY",
                            "volume": 69642.0,
                            "openPrice": 11840.2394,
                            "avgPrice": 11840.3095,
                            "closePrice": 12155.3005,
                            "leverageLevel": 24,
                            "holdAmount": 7014.2111,
                            "closeVolume": 40502.0,
                            "pendingCloseVolume": 0,
                            "realizedAmount": 8115.9125,
                            "historyRealizedAmount": 1865.3985,
                            "tradeFee": -432.0072,
                            "capitalFee": 2891.2281,
                            "closeProfit": 8117.6903,
                            "shareAmount": 0.1112,
                            "freezeLock": 0,
                            "status": 1,
                            "ctime": "2020-12-11T17:42:10",
                            "mtime": "2020-12-18T20:35:43",
                            "brokerId": 21,
                            "marginRate": 0.2097,
                            "reducePrice": 9740.8083,
                            "returnRate": 0.3086,
                            "unRealizedAmount": 2164.5289,
                            "openRealizedAmount": 2165.0173,
                            "positionBalance": 82458.2839,
                            "settleProfit": 0.4883,
                            "indexPrice": 12151.1175,
                            "keepRate": 0.005,
                            "maxFeeRate": 0.0025
                        }
                    ]
                }
            ]
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

#### Response: <a href="#response-10" id="response-10"></a>

| name      | type | description        |
| --------- | ---- | ------------------ |
| `account` | `[]` | Balance collection |

`account` field:

| name                | type   | example | description                        |
| ------------------- | ------ | ------- | ---------------------------------- |
| marginCoin          | string | USDT    | Margin coin                        |
| accountNormal       | float  | 10.05   | Balance account                    |
| accountLock         | float  | 10.07   | Margin frozen account              |
| partPositionNormal  | float  | 10.07   | Restricted position margin balance |
| totalPositionNormal | float  | 10.07   | Full position initial margin       |
| achievedAmount      | float  | 10.07   | Profit and losses occurred         |
| unrealizedAmount    | float  | 10.05   | Unfilled profit and losses         |
| totalMarginRate     | float  | 10.05   | Full position margin rate          |
| totalEquity         | float  | 10.07   | Full position equity               |
| partEquity          | float  | 10.07   | Restricted position equity         |
| totalCost           | float  | 10.07   | Full position costs                |
| sumMarginRate       | float  | 10.07   | All accounts margin rate           |
| positionVos         | \[ ]   | ​       | Position contract record           |

`positionVos` field:

| name           | type    | example    | description        |
| -------------- | ------- | ---------- | ------------------ |
| contractId     | integer | 2          | Contract id        |
| contractName   | string  | E-BTC-USDT | Contract name      |
| contractSymbol | string  | BTC-USDT   | Contract coin pair |
| positions      | \[ ]    | ​          | Position details   |

`positions` field:

| name                  | type    | example | description                                                               |
| --------------------- | ------- | ------- | ------------------------------------------------------------------------- |
| id                    | integer | 2       | Position id                                                               |
| uid                   | integer | 10023   | User ID                                                                   |
| positionType          | integer | 1       | Hold position type(1 full，2 restrictive)                                  |
| side                  | string  | SELL    | Hold position direction BUY sell long, SELL buy short                     |
| volume                | float   | 1.05    | Hold quantity                                                             |
| openPrice             | float   | 1.05    | Open position price                                                       |
| avgPrice              | float   | 1.05    | Hold average price                                                        |
| closePrice            | float   | 1.05    | Balancing average price                                                   |
| leverageLevel         | float   | 1.05    | Leverage multiple                                                         |
| holdAmount            | float   | 1.05    | Hold position margin                                                      |
| closeVolume           | float   | 1.05    | Balanced quantity                                                         |
| pendingCloseVolume    | float   | 1.05    | The number of pending closing orders                                      |
| realizedAmount        | float   | 1.05    | Profit and losses occurred                                                |
| historyRealizedAmount | float   | 1.05    | Historic accumulated profit and losses                                    |
| tradeFee              | float   | 1.05    | Trading fees                                                              |
| capitalFee            | float   | 1.05    | Capital costs                                                             |
| closeProfit           | float   | 1.05    | Balancing profit and loss                                                 |
| shareAmount           | float   | 1.05    | Amount to share                                                           |
| freezeLock            | integer | 0       | Position freeze status: 0 normal, 1 liquidation freeze, 2 delivery freeze |
| status                | integer | 0       | Position effectiveness，0 ineffective 1 effective                          |
| ctime                 | time    | ​       | Creation time                                                             |
| mtime                 | time    | ​       | Update time                                                               |
| brokerId              | integer | 1023    | Client id                                                                 |
| lockTime              | time    | ​       | liquidation lock time                                                     |
| marginRate            | float   | 1.05    | Margin rate                                                               |
| reducePrice           | float   | 1.05    | Price reduction                                                           |
| returnRate            | float   | 1.05    | Return rate (profit rate)                                                 |
| unRealizedAmount      | float   | 1.05    | Unfilled profit and losses                                                |
| openRealizedAmount    | float   | 1.05    | Open position unfilled  profit and losses                                 |
| positionBalance       | float   | 1.05    | Position value                                                            |
| indexPrice            | float   | 1.05    | Newest marked price                                                       |
| keepRate              | float   | 1.05    | Scaled minimum kept margin rate                                           |
| maxFeeRate            | float   | 1.05    | <p>Balancing maximum fees rate<br></p>                                    |
