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

<table data-header-hidden><thead><tr><th width="150">name</th><th>type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>time</td><td>long</td><td><code>1595563624731</code></td><td>Open Time</td><td></td></tr><tr><td>high</td><td>float</td><td><code>9900</code></td><td>High Price</td><td></td></tr><tr><td>low</td><td>float</td><td><code>8800.34</code></td><td>Low Price</td><td></td></tr><tr><td>open</td><td>float</td><td><code>8700</code></td><td>Open Price</td><td></td></tr><tr><td>last</td><td>float</td><td><code>8900</code></td><td>Last Price</td><td></td></tr><tr><td>vol</td><td>float</td><td><code>4999</code></td><td>Trade Volume</td><td></td></tr><tr><td>rose</td><td>float</td><td>0</td><td>Price increase or Price rise</td><td></td></tr></tbody></table>





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

<table data-header-hidden><thead><tr><th width="150">name</th><th>type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>price</td><td>float</td><td><code>0.055</code></td><td>The price of the trade</td><td></td></tr><tr><td>time</td><td>long</td><td><code>1537797044116</code></td><td>Current timestamp (ms)</td><td></td></tr><tr><td>qty</td><td>float</td><td><code>5</code></td><td>The quantity traded</td><td></td></tr><tr><td>side</td><td>string</td><td><code>BUY/SELL</code></td><td>Taker side</td><td></td></tr></tbody></table>





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

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td><code>idx</code></td><td>long</td><td><code>1538728740000</code></td><td>Open time</td><td></td></tr><tr><td>open</td><td>float</td><td><code>36.00000</code></td><td>open price</td><td></td></tr><tr><td>close</td><td>float</td><td><code>33.00000</code></td><td>close price</td><td></td></tr><tr><td>high</td><td>float</td><td><code>36.00000</code></td><td>high price</td><td></td></tr><tr><td>low</td><td>float</td><td><code>30.00000</code></td><td>low price</td><td></td></tr><tr><td>vol</td><td>float</td><td><code>2456.111</code></td><td>volume</td><td></td></tr></tbody></table>

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
    'orderId': 150695552109032492, 
    'orderIdString': '150695552109032492',//Character String Type Order ID (Recommended)
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

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>orderId</td><td>long</td><td><code>150695552109032492</code></td><td>ID of the order</td><td></td></tr><tr><td>clientorderId</td><td>string</td><td><code>213443</code></td><td>A unique ID of the order.</td><td></td></tr><tr><td>symbol</td><td>string</td><td><code>BTCUSDT</code></td><td>Symbol Name</td><td></td></tr><tr><td>transactTime</td><td>integer</td><td><code>1273774892913</code></td><td>Time the order is placed</td><td></td></tr><tr><td>price</td><td>float</td><td><code>4765.29</code></td><td>Time the order is placed</td><td></td></tr><tr><td>origQty</td><td>float</td><td><code>1.01</code></td><td>Quantity ordered</td><td></td></tr><tr><td>executedQty</td><td>float</td><td><code>1.01</code></td><td>Quantity of orders that has been executed</td><td></td></tr><tr><td>type</td><td>string</td><td><code>LIMIT</code></td><td>Order type <code>LIMIT,MARKET</code></td><td></td></tr><tr><td>side</td><td>string</td><td><code>BUY</code></td><td>Order side：<code>BUY, SELL</code></td><td></td></tr><tr><td>status</td><td>string</td><td><code>NEW</code></td><td>The state of the order.Possible values include <code>NEW</code>, <code>PARTIALLY_FILLED</code>, <code>FILLED</code>, <code>CANCELED</code>, and <code>REJECTED</code>.POST</td><td></td></tr></tbody></table>

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
    "idsString": [ //Character String Type Order ID (Recommended)
        "165964665990709251",
        "165964665990709252",
        "165964665990709253"
    ],
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

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>price</td><td>long</td><td>1000</td><td>Price of the order</td><td></td></tr><tr><td>volume</td><td>folat</td><td>20.1</td><td>Vol of the order</td><td></td></tr><tr><td>side</td><td>string</td><td><code>BUY/SELL</code></td><td>Side of the order</td><td></td></tr><tr><td>batchType</td><td>string</td><td><code>LIMIT/MARKET</code></td><td>Batch type of the order</td><td></td></tr></tbody></table>





{% swagger method="get" path="/sapi/v1/order" baseUrl="https://openapi.xxx.com" summary=" Query Order" %}
{% swagger-description %}

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

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>Example</th><th>Description</th><th></th></tr></thead><tbody><tr><td>orderId</td><td>long</td><td><code>150695552109032492</code></td><td>Order ID (system generated)</td><td></td></tr><tr><td>clientorderId</td><td>string</td><td><code>213443</code></td><td>Order ID (sent by yourself)</td><td></td></tr><tr><td>symbol</td><td>string</td><td><code>BTCUSDT</code></td><td>Currency Pair Name</td><td></td></tr><tr><td>price</td><td>float</td><td><code>4765.29</code></td><td>Order Price</td><td></td></tr><tr><td>origQty</td><td>float</td><td><code>1.01</code></td><td>Number of orders</td><td></td></tr><tr><td>executedQty</td><td>float</td><td><code>1.01</code></td><td>Number of orders already filled</td><td></td></tr><tr><td>avgPrice</td><td>float</td><td><code>4754.24</code></td><td>Average price of orders already filled</td><td></td></tr><tr><td>type</td><td>string</td><td>limit</td><td>The order type<code>LIMIT,MARKET</code></td><td></td></tr><tr><td>side</td><td>string</td><td><code>BUY</code></td><td>Order direction. Possible values can only be: BUY (buy long) and SELL (sell short)</td><td></td></tr><tr><td>status</td><td>string</td><td><code>NEW</code></td><td>Order status. Possible values are NEW (new order, no transaction), PARTIALLY_FILLED (partially filled), FILLED (fully filled), CANCELED (cancelled) and REJECTED (order rejected).POST</td><td></td></tr><tr><td>transactTime</td><td>string</td><td>1574327555669</td><td>Order Creation Time</td><td></td></tr></tbody></table>





{% swagger method="post" path="/sapi/v1/cancel" baseUrl="https://openapi.xxx.com" summary="Cancel Order" %}
{% swagger-description %}

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

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>orderId</td><td>long</td><td><code>150695552109032492</code></td><td>ID of the order</td><td></td></tr><tr><td>clientorderId</td><td>string</td><td><code>213443</code></td><td>Unique ID of the order.</td><td></td></tr><tr><td>symbol</td><td>string</td><td><code>BTCUSDT</code></td><td>Name of the symbol</td><td></td></tr><tr><td>status</td><td>string</td><td><code>NEW</code></td><td>The state of the order.Possible values include <code>NEW</code>, <code>PARTIALLY_FILLED</code>, <code>FILLED</code>, <code>CANCELED</code>, and <code>REJECTED</code>.POST<br></td><td></td></tr></tbody></table>





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
        'orderId': 499902955766523648, 
        'orderIdString': '499902955766523648', //Character String Type Order ID (Recommended)
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

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>orderId</td><td>long</td><td><code>150695552109032492</code></td><td>ID of the order</td><td></td></tr><tr><td>orderIdString</td><td>string</td><td>"<code>150695552109032492"</code></td><td>Character String Type Order ID (Recommended)</td><td></td></tr><tr><td>clientorderId</td><td>string</td><td><code>213443</code></td><td>Unique ID of the order.</td><td></td></tr><tr><td>symbol</td><td>string</td><td><code>BTCUSDT</code></td><td>Name of the symbol</td><td></td></tr><tr><td>price</td><td>float</td><td><code>4765.29</code></td><td>Price of the order</td><td></td></tr><tr><td>origQty</td><td>float</td><td><code>1.01</code></td><td>Quantity ordered</td><td></td></tr><tr><td>executedQty</td><td>float</td><td><code>1.01</code></td><td>Quantity of orders that has been executed</td><td></td></tr><tr><td>avgPrice</td><td>float</td><td><code>4754.24</code></td><td>Average price of filled orders.</td><td></td></tr><tr><td>type</td><td>string</td><td><code>LIMIT</code></td><td>The order type<code>LIMIT,MARKET</code></td><td></td></tr><tr><td>side</td><td>string</td><td><code>BUY</code></td><td>The order side <code>BUY,SELL</code></td><td></td></tr><tr><td>status</td><td>string</td><td><code>NEW</code></td><td>The state of the order.Possible values include <code>NEW</code>, <code>PARTIALLY_FILLED</code>, <code>FILLED</code>, <code>CANCELED</code>, and <code>REJECTED</code>.GET</td><td></td></tr><tr><td>time</td><td>string</td><td>1574327555669</td><td>Creation Time</td><td></td></tr></tbody></table>



{% swagger method="get" path="/sapi/v1/myTrades" baseUrl="https://openapi.xxx.com" summary="Trades" %}
{% swagger-description %}

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
    "fee":"0.001",
    "bidUserId":23334,
    "askUserId":44112
  },...
]
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 1**

#### **Response:**

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th></tr></thead><tbody><tr><td>symbol</td><td>string</td><td><code>BTCUSDT</code></td><td>Name of the symbol</td></tr><tr><td>id</td><td>integer</td><td><code>28457</code></td><td>Trade ID</td></tr><tr><td>bidId</td><td>long</td><td><code>150695552109032492</code></td><td>Bid Order ID</td></tr><tr><td>askId</td><td>long</td><td><code>150695552109032492</code></td><td>Ask Order ID</td></tr><tr><td>price</td><td>integer</td><td><code>4.01</code></td><td>Price of the trade</td></tr><tr><td>qty</td><td>float</td><td><code>12</code></td><td>Quantiry of the trade</td></tr><tr><td>time</td><td>number</td><td><code>1499865549590</code></td><td>timestamp of the trade</td></tr><tr><td>isBuyer</td><td>bool</td><td><code>true</code></td><td><code>true</code>= Buyer <code>false</code>= Seller</td></tr><tr><td>isMaker</td><td>bool</td><td><code>false</code></td><td><code>true</code>=Maker <code>false</code>=Taker</td></tr><tr><td>feeCoin</td><td>string</td><td><code>ETH</code></td><td>Trading fee coin</td></tr><tr><td>fee</td><td>number</td><td><code>0.001</code></td><td>Trading fee</td></tr><tr><td>bidUserId</td><td>long</td><td>23334</td><td>Buyer UID</td></tr><tr><td>askUserId</td><td>long</td><td>44112</td><td>Seller UID</td></tr></tbody></table>



## Account

### Security Type: USER\_DATA

Endpoints under Account require an API-key and a signature.\


{% swagger method="get" path="/sapi/v1/account" baseUrl="https://openapi.xxx.com" summary=" Account Information" %}
{% swagger-description %}

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
