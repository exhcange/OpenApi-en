# Spot

## Public

### Security: [None](broken-reference)

{% swagger method="get" path="/sapi/v1/ping" baseUrl="https://openapi.xxx.com" summary=" Test Connectivity" %}
{% swagger-description %}
 This endpoint checks connectivity to the host
{% endswagger-description %}

{% swagger-response status="200: OK" description=" Connection normal" %}
```javascript
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/sapi/v1/time" baseUrl="https://openapi.xxx.com" summary=" Check Server Time" %}
{% swagger-description %}
 This endpoint checks connectivity to the server and retrieves server timestamp
{% endswagger-description %}

{% swagger-response status="200: OK" description=" Successfully retrieved server time" %}
```javascript
{
    "timezone": "GMT+08:00",
    "serverTime": 1595563624731
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/sapi/v1/symbols" baseUrl="https://openapi.xxx.com" summary="Pairs List " %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "symbols": [
        {
            "quantityPrecision": 3,
            "symbol": "sccadai",
            "pricePrecision": 6,
            "baseAsset": "SCCA",
            "quoteAsset": "DAI"
        },
        {
            "quantityPrecision": 8,
            "symbol": "btcusdt",
            "pricePrecision": 2,
            "baseAsset": "BTC",
            "quoteAsset": "USDT"
        },
        {
            "quantityPrecision": 3,
            "symbol": "bchusdt",
            "pricePrecision": 2,
            "baseAsset": "BCH",
            "quoteAsset": "USDT"
        },
        {
            "quantityPrecision": 2,
            "symbol": "etcusdt",
            "pricePrecision": 2,
            "baseAsset": "ETC",
            "quoteAsset": "USDT"
        },
        {
            "quantityPrecision": 2,
            "symbol": "ltcbtc",
            "pricePrecision": 6,
            "baseAsset": "LTC",
            "quoteAsset": "BTC"
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 1**

#### Response: <a href="#bi-dui-lie-biao" id="bi-dui-lie-biao"></a>

| symbol            | string  | `BTCUSDT` | Name of the symbol              |   | Currency to name  |
| ----------------- | ------- | --------- | ------------------------------- | - | ----------------- |
| baseAsset         | string  | `BTC`     | Underlying asset for the symbol |   | base currency     |
| quoteAsset        | string  | `USDT`    | Quote asset for the symbol      |   | The base currency |
| pricePrecision    | integer | `2`       | Precision of the price          |   | Price Accuracy    |
| quantityPrecision | integer | `6`       | Precision of the quantity       |   | Quantity accuracy |

## Market

### Security Type: [None](broken-reference)

{% swagger method="get" path="/sapi/v1/depth" baseUrl="https://openapi.xxx.com" summary=" Depth" %}
{% swagger-description %}
 market detpth data
{% endswagger-description %}

{% swagger-parameter in="query" name="limit" type="integer" %}
Default 100; Max 100
{% endswagger-parameter %}

{% swagger-parameter in="query" name="symbol" type="String" required="true" %}
Symbol Name E.g. BTCUSDT
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" Successfully retrieved market depth data" %}
```javascript
{
  "bids": [
    [
      "3.90000000",   // price
      "431.00000000"  // vol
    ],
    [
      "4.00000000",
      "431.00000000"
    ]
  ],
  "asks": [
    [
      "4.00000200",  // price
      "12.00000000"  // vol
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

**weight(IP/UID): 5**

#### Response: <a href="#bi-dui-lie-biao" id="bi-dui-lie-biao"></a>

| time | long | `1595563624731` | Current timestamp (ms)                                          |
| ---- | ---- | --------------- | --------------------------------------------------------------- |
| bids | list | ;               | List of all bids, best bids first. See below for entry details. |
| asks | list | ;               | List of all asks, best asks first. See below for entry details. |

The fields bids and asks are lists of order book price level entries, sorted from best to worst.

| ' ' | float | `131.1` | price level                                       |
| --- | ----- | ------- | ------------------------------------------------- |
| ' ' | float | `2.3`   | The total quantity of orders for this price level |





{% swagger method="get" path="/sapi/v1/ticker" baseUrl="https://openapi.xxx.com" summary=" 24hrs ticker" %}
{% swagger-description %}
 24 hour price change statistics.
{% endswagger-description %}

{% swagger-parameter in="query" name="symbol" required="true" %}
Symbol Name. E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" Successfully retrieved ticker data" %}
```javascript
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

**weight(IP/UID): 5**

#### Response:

| time | long  | `1595563624731` | Open Time    |   |
| ---- | ----- | --------------- | ------------ | - |
| high | float | `9900`          | High Price   |   |
| low  | float | `8800.34`       | Low Price    |   |
| open | float | `8700`          | Open Price   |   |
| last | float | `8900`          | Last Price   |   |
| vol  | float | `4999`          | Trade Volume |   |





{% swagger method="get" path="/sapi/v1/trades" baseUrl="https://openapi.xxx.com" summary="Recent Trades List" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="symbol" required="true" %}
Symbol Name. E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" %}
Default 100; Max 1000Responses200
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "list":[
        {
            "price":"3.00000100",
            "qty":"11.00000000",
            "time":1499865549590,
            "side":"BUY"
        }
    ]
}
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 5**

#### Response:

| price | float  | `0.055`         | The price of the trade |   |
| ----- | ------ | --------------- | ---------------------- | - |
| time  | long   | `1537797044116` | Current timestamp (ms) |   |
| qty   | float  | `5`             | The quantity traded    |   |
| side  | string | `BUY/SELL`      | Taker side             |   |





{% swagger method="get" path="/sapi/v1/klines" baseUrl="https://openapi.xxx.com" summary="Kline/candlestick data" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="symbol" type="" required="true" %}
Symbol Name. E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="interval" required="true" %}
Interval of the Kline. Possible values include: 

`1min`

,

`5min`

,

`15min`

,

`30min`

,

`60min`

,

`1day`

,

`1week`

,

`1month`

\



{% endswagger-parameter %}

{% swagger-parameter in="query" name=" Default 100; Max 300" %}
Default 100; Max 300Responses200
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
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

**weight(IP/UID): 1**

#### Response:

| `idx` | long  | `1538728740000` | Open time   |   |
| ----- | ----- | --------------- | ----------- | - |
| open  | float | `36.00000`      | open price  |   |
| close | float | `33.00000`      | close price |   |
| high  | float | `36.00000`      | high price  |   |
| low   | float | `30.00000`      | low price   |   |
| vol   | float | `2456.111`      | volume      |   |

### Trade

### Security Type: [TRADE](broken-reference)

Endpoints under **Trade** require an API Key and a signature

{% swagger method="post" path="/sapi/v1/order" baseUrl="https://openapi.xxx.com" summary=" New Order" %}
{% swagger-description %}
 

**Rate Limit: 100times/2s**
{% endswagger-description %}

{% swagger-parameter in="query" name="X-CH-SIGN" type="string" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="query" name="X-CH-APIKEY" type="string" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="query" name="X-CH-TS" type="integer" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" required="true" %}
Symbol Name. E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="volume" type="number" required="true" %}
Order vol. For MARKET BUY orders, vol=amount.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="side" required="true" %}
Side of the order,

`BUY/SELL`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" required="true" %}
Type of the order, 

`LIMIT/MARKET`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="number" required="true" %}
Order price, REQUIRED for LIMIT orders
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newClientOrderId" %}
Unique order ID generated by users to mark their orders
{% endswagger-parameter %}

{% swagger-parameter in="body" name="recvwindow" type="integer" %}
Time window
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" Successfully post new order" %}
```javascript
{
    'symbol': 'LXTUSDT', 
    'orderId': '150695552109032492', 
    'clientOrderId': '157371322565051',
    'transactTime': '1573713225668', 
    'price': '0.005452', 
    'origQty': '110', 
    'executedQty': '0', 
    'status': 'NEW',
    'type': 'LIMIT', 
    'side': 'SELL'
}
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 5**

#### Response:

| orderId       | long    | `150695552109032492` | ID of the order                                                                                                     |   |
| ------------- | ------- | -------------------- | ------------------------------------------------------------------------------------------------------------------- | - |
| clientorderId | string  | `213443`             | A unique ID of the order.                                                                                           |   |
| symbol        | string  | `BTCUSDT`            | Symbol Name                                                                                                         |   |
| transactTime  | integer | `1273774892913`      | Time the order is placed                                                                                            |   |
| price         | float   | `4765.29`            | Time the order is placed                                                                                            |   |
| origQty       | float   | `1.01`               | Quantity ordered                                                                                                    |   |
| executedQty   | float   | `1.01`               | Quantity of orders that has been executed                                                                           |   |
| type          | string  | `LIMIT`              | Order type `LIMIT,MARKET`                                                                                           |   |
| side          | string  | `BUY`                | Order side：`BUY, SELL`                                                                                              |   |
| status        | string  | `NEW`                | The state of the order.Possible values include `NEW`, `PARTIALLY_FILLED`, `FILLED`, `CANCELED`, and `REJECTED`.POST |   |

{% swagger method="post" path="/sapi/v1/order/test" baseUrl="https://openapi.xxx.com" summary=" Test New Order" %}
{% swagger-description %}
 Test new order creation and signature/recvWindow length. Creates and validates a new order but does not send the order into the matching engine.
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="recvwindow" type="integer" %}
Time window
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" required="true" %}
Symbol Name. E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="volume" type="number" required="true" %}
Order vol. For MARKET BUY orders, vol=amount.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="side" required="true" %}
Side of the order, 

`BUY/SELL`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="type" required="true" %}
Type of the order, 

`LIMIT/MARKET`
{% endswagger-parameter %}

{% swagger-parameter in="body" name="price" type="number" required="true" %}
Order price, REQUIRED for 

`LIMIT`

 orders
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newClientorderId" %}
Unique order ID generated by users to mark their orders
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" Successfully test new order" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 1**

****



{% swagger method="post" path="/sapi/v1/batchOrders" baseUrl="https://openapi.xxx.com" summary=" Batch Orders" %}
{% swagger-description %}
 

**batch contains at most 10 orders**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" required="true" %}
Batch order param
{% endswagger-parameter %}

{% swagger-parameter in="body" name="orders" type="number" %}
Symbol Name. E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "ids": [
        165964665990709251,
        165964665990709252,
        165964665990709253
    ]
}
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 10**

#### Resquest `orders` field: <a href="#resquest-orders-field" id="resquest-orders-field"></a>

| price     | long   | 1000           | Price of the order      |   |
| --------- | ------ | -------------- | ----------------------- | - |
| volume    | folat  | 20.1           | Vol of the order        |   |
| side      | string | `BUY/SELL`     | Side of the order       |   |
| batchType | string | `LIMIT/MARKET` | Batch type of the order |   |





{% swagger method="get" path="/sapi/v1/order" baseUrl="https://openapi.xxx.com" summary=" Query Order" %}
{% swagger-description %}
 

**Rate Limit: 20times/2s**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
timestampResponses200
{% endswagger-parameter %}

{% swagger-parameter in="query" name="orderId" required="true" %}
Order ID
{% endswagger-parameter %}

{% swagger-parameter in="query" name="newClientorderId" %}
Client Order Id, Unique order ID generated by users to mark their orders. E.g. 354444heihieddada
{% endswagger-parameter %}

{% swagger-parameter in="query" name="symbol" required="true" %}
Symbol Name. E.g. 

`BTCUSDl`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    'orderId': '499890200602846976', 
    'clientOrderId': '157432755564968', 
    'symbol': 'BHTUSDT', 
    'price': '0.01', 
    'origQty': '50', 
    'executedQty': '0', 
    'avgPrice': '0', 
    'status': 'NEW', 
    'type': 'LIMIT', 
    'side': 'BUY', 
    'transactTime': '1574327555669'
}
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 1**

#### **Response:**

| orderId       | long   | `150695552109032492` | Order ID (system generated)                                                                                                                                                             |   |
| ------------- | ------ | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | - |
| clientorderId | string | `213443`             | Order ID (sent by yourself)                                                                                                                                                             |   |
| symbol        | string | `BTCUSDT`            | Currency Pair Name                                                                                                                                                                      |   |
| price         | float  | `4765.29`            | Order Price                                                                                                                                                                             |   |
| origQty       | float  | `1.01`               | Number of orders                                                                                                                                                                        |   |
| executedQty   | float  | `1.01`               | Number of orders already filled                                                                                                                                                         |   |
| avgPrice      | float  | `4754.24`            | Average price of orders already filled                                                                                                                                                  |   |
| type          | string | limit                | The order type`LIMIT,MARKET`                                                                                                                                                            |   |
| side          | string | `BUY`                | Order direction. Possible values can only be: BUY (buy long) and SELL (sell short)                                                                                                      |   |
| status        | string | `NEW`                | Order status. Possible values are NEW (new order, no transaction), PARTIALLY\_FILLED (partially filled), FILLED (fully filled), CANCELED (cancelled) and REJECTED (order rejected).POST |   |





{% swagger method="post" path="/sapi/v1/cancel" baseUrl="https://openapi.xxx.com" summary="Cancel Order" %}
{% swagger-description %}
 

**Rate Limit: 100time/2s**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="orderId" required="true" %}
Order ID
{% endswagger-parameter %}

{% swagger-parameter in="body" name="newClientOrderId" type="String" %}
Client Order Id, Unique order ID generated by users to mark their orders. E.g. 354444heihieddada
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" required="true" %}
Symbol Name. E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    'symbol': 'BHTUSDT', 
    'clientOrderId': '0', 
    'orderId': '499890200602846976', 
    'status': 'CANCELED'
}

```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 5**

#### Response:

| orderId       | long   | `150695552109032492` | ID of the order                                                                                                                                                                       |   |
| ------------- | ------ | -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | - |
| clientorderId | string | `213443`             | Unique ID of the order.                                                                                                                                                               |   |
| symbol        | string | `BTCUSDT`            | Name of the symbol                                                                                                                                                                    |   |
| status        | string | `NEW`                | <p>The state of the order.Possible values include <code>NEW</code>, <code>PARTIALLY_FILLED</code>, <code>FILLED</code>, <code>CANCELED</code>, and <code>REJECTED</code>.POST<br></p> |   |





{% swagger method="post" path="/sapi/v1/batchCancel" baseUrl="https://openapi.xxx.com" summary=" Batch cancel orders" %}
{% swagger-description %}
 

**batch contains at most 10 orders**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="orderIds" %}
Order ID collection 

`[123,456]`

Responses200GET
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" required="true" %}
Symbol Name. E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    "success": [
        165964665990709251,
        165964665990709252,
        165964665990709253
    ],
    "failed": [ //cancel fails because the order does not exist or the order state has expired
        165964665990709250  
    ]
}
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 10**

{% swagger method="get" path="/sapi/v1/openOrders" baseUrl="https://openapi.xxx.com" summary=" Current Open Orders" %}
{% swagger-description %}
**Rate Limit: 20times/2s**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="query" name="symbol" required="true" %}
Symbol Name. E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" %}
Default 100; Max 1000
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
[
    {
        'orderId': '499902955766523648', 
        'symbol': 'BHTUSDT', 
        'price': '0.01', 
        'origQty': '50', 
        'executedQty': '0', 
        'avgPrice': '0', 
        'status': 'NEW', 
        'type': 'LIMIT', 
        'side': 'BUY', 
        'time': '1574329076202'
        },...
]
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 1**

#### **Response:**

| orderId       | long   | `150695552109032492` | ID of the order                                                                                                    |   |
| ------------- | ------ | -------------------- | ------------------------------------------------------------------------------------------------------------------ | - |
| clientorderId | string | `213443`             | Unique ID of the order.                                                                                            |   |
| symbol        | string | `BTCUSDT`            | Name of the symbol                                                                                                 |   |
| price         | float  | `4765.29`            | Price of the order                                                                                                 |   |
| origQty       | float  | `1.01`               | Quantity ordered                                                                                                   |   |
| executedQty   | float  | `1.01`               | Quantity of orders that has been executed                                                                          |   |
| avgPrice      | float  | `4754.24`            | Average price of filled orders.                                                                                    |   |
| type          | string | `LIMIT`              | The order type`LIMIT,MARKET`                                                                                       |   |
| side          | string | `BUY`                | The order side `BUY,SELL`                                                                                          |   |
| status        | string | `NEW`                | The state of the order.Possible values include `NEW`, `PARTIALLY_FILLED`, `FILLED`, `CANCELED`, and `REJECTED`.GET |   |



{% swagger method="get" path="/sapi/v1/myTrades" baseUrl="https://openapi.xxx.com" summary="Trades" %}
{% swagger-description %}
 

**Rate Limt: 20times/2s**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="query" name="symbol" required="true" %}
Symbol Name. E.g. 

`BTCUSDT`
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" %}
Default 100; Max1000
{% endswagger-parameter %}

{% swagger-parameter in="query" name="fromId" %}
Trade Id to fetch from
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
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
    "feeCoin": "ETH",
    "fee":"0.001"
  },...
]
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 1**

#### **Response:**

| symbol  | string  | `BTCUSDT`            | Name of the symbol            |
| ------- | ------- | -------------------- | ----------------------------- |
| id      | integer | `28457`              | Trade ID                      |
| bidId   | long    | `150695552109032492` | Bid Order ID                  |
| askId   | long    | `150695552109032492` | Ask Order ID                  |
| price   | integer | `4.01`               | Price of the trade            |
| qty     | float   | `12`                 | Quantiry of the trade         |
| time    | number  | `1499865549590`      | timestamp of the trade        |
| isBuyer | bool    | `true`               | `true`= Buyer `false`= Seller |
| isMaker | bool    | `false`              | `true`=Maker `false`=Taker    |
| feeCoin | string  | `ETH`                | Trading fee coin              |
| fee     | number  | `0.001`              | Trading fee                   |

****

## Account

### Security Type: USER\_DATA

Endpoints under Account require an API-key and a signature.\


{% swagger method="get" path="/sapi/v1/account" baseUrl="https://openapi.xxx.com" summary=" Account Information" %}
{% swagger-description %}
 

**Rate Limit: 20times/2s**
{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-SIGN" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-APIKEY" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" %}
timestamp
{% endswagger-parameter %}

{% swagger-response status="200: OK" description=" Successfully retrieved account information." %}
```javascript
{
    'balances': 
        [
            {
                'asset': 'BTC', 
                'free': '0', 
                'locked': '0'
                }, 
            {
                'asset': 'ETH', 
                'free': '0', 
                'locked': '0'
                },...
        ]
}
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 1**

#### Response: <a href="#response-10" id="response-10"></a>

| name       | type | description          |
| ---------- | ---- | -------------------- |
| `balances` | \[]  | Show balance details |

`balances` field:

| name     | type   | example | description                     |
| -------- | ------ | ------- | ------------------------------- |
| `asset`  | string | `USDT`  | Name of the asset               |
| `free`   | float  | 1000.30 | Amount available for use        |
| `locked` | float  | 400     | Amount locked (for open orders) |
