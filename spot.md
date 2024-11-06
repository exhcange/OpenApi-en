# Spot

## Public

### Security: [None](broken-reference)

## &#x20;Test Connectivity

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/ping`

&#x20;This endpoint checks connectivity to the host

{% tabs %}
{% tab title="200: OK  Connection normal" %}
```javascript
}
```
{% endtab %}
{% endtabs %}

## &#x20;Check Server Time

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/time`

&#x20;This endpoint checks connectivity to the server and retrieves server timestamp

{% tabs %}
{% tab title="200: OK  Successfully retrieved server time" %}
```javascript
{
    "timezone": "GMT+08:00",
    "serverTime": 1595563624731
}
```
{% endtab %}
{% endtabs %}

## Pairs List&#x20;

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/symbols`

{% tabs %}
{% tab title="200: OK " %}
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
{% endtab %}
{% endtabs %}

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

## &#x20;Depth

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/depth`

&#x20;market detpth data

#### Query Parameters

| Name                                     | Type    | Description              |
| ---------------------------------------- | ------- | ------------------------ |
| limit                                    | integer | Default 100; Max 100     |
| symbol<mark style="color:red;">\*</mark> | String  | Symbol Name E.g. BTCUSDT |

{% tabs %}
{% tab title="200: OK  Successfully retrieved market depth data" %}
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
{% endtab %}
{% endtabs %}

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





## &#x20;24hrs ticker

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/ticker`

&#x20;24 hour price change statistics.

#### Query Parameters

| Name                                     | Type   | Description                 |
| ---------------------------------------- | ------ | --------------------------- |
| symbol<mark style="color:red;">\*</mark> | String | Symbol Name. E.g. `BTCUSDT` |

{% tabs %}
{% tab title="200: OK  Successfully retrieved ticker data" %}
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
{% endtab %}
{% endtabs %}

**weight(IP/UID): 5**

#### Response:

<table data-header-hidden><thead><tr><th width="150">name</th><th>type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>time</td><td>long</td><td><code>1595563624731</code></td><td>Open Time</td><td></td></tr><tr><td>high</td><td>float</td><td><code>9900</code></td><td>High Price</td><td></td></tr><tr><td>low</td><td>float</td><td><code>8800.34</code></td><td>Low Price</td><td></td></tr><tr><td>open</td><td>float</td><td><code>8700</code></td><td>Open Price</td><td></td></tr><tr><td>last</td><td>float</td><td><code>8900</code></td><td>Last Price</td><td></td></tr><tr><td>vol</td><td>float</td><td><code>4999</code></td><td>Trade Volume</td><td></td></tr><tr><td>rose</td><td>float</td><td>0</td><td>Price increase or Price rise</td><td></td></tr></tbody></table>





## Recent Trades List

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/trades`

#### Query Parameters

| Name                                     | Type   | Description                       |
| ---------------------------------------- | ------ | --------------------------------- |
| symbol<mark style="color:red;">\*</mark> | String | Symbol Name. E.g. `BTCUSDT`       |
| limit                                    | String | Default 100; Max 1000Responses200 |

{% tabs %}
{% tab title="200: OK " %}
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
{% endtab %}
{% endtabs %}

**weight(IP/UID): 5**

#### Response:

<table data-header-hidden><thead><tr><th width="150">name</th><th>type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>price</td><td>float</td><td><code>0.055</code></td><td>The price of the trade</td><td></td></tr><tr><td>time</td><td>long</td><td><code>1537797044116</code></td><td>Current timestamp (ms)</td><td></td></tr><tr><td>qty</td><td>float</td><td><code>5</code></td><td>The quantity traded</td><td></td></tr><tr><td>side</td><td>string</td><td><code>BUY/SELL</code></td><td>Taker side</td><td></td></tr></tbody></table>





## Kline/candlestick data

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/klines`

#### Query Parameters

| Name                                       | Type   | Description                                                                                                                                                                                                      |
| ------------------------------------------ | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| symbol<mark style="color:red;">\*</mark>   |        | Symbol Name. E.g. `BTCUSDT`                                                                                                                                                                                      |
| interval<mark style="color:red;">\*</mark> | String | <p>Interval of the Kline. Possible values include: <code>1min</code>,<code>5min</code>,<code>15min</code>,<code>30min</code>,<code>60min</code>,<code>1day</code>,<code>1week</code>,<code>1month</code><br></p> |
|  Default 100; Max 300                      | String | Default 100; Max 300Responses200                                                                                                                                                                                 |
| startTime                                  | long   | startTime  example:`1538728740000`                                                                                                                                                                               |
| endTime                                    | long   | endTime example:`1538728740000`                                                                                                                                                                                  |

{% tabs %}
{% tab title="200: OK " %}
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
{% endtab %}
{% endtabs %}

**weight(IP/UID): 1**

#### Response:

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td><code>idx</code></td><td>long</td><td><code>1538728740000</code></td><td>Open time</td><td></td></tr><tr><td>open</td><td>float</td><td><code>36.00000</code></td><td>open price</td><td></td></tr><tr><td>close</td><td>float</td><td><code>33.00000</code></td><td>close price</td><td></td></tr><tr><td>high</td><td>float</td><td><code>36.00000</code></td><td>high price</td><td></td></tr><tr><td>low</td><td>float</td><td><code>30.00000</code></td><td>low price</td><td></td></tr><tr><td>vol</td><td>float</td><td><code>2456.111</code></td><td>volume</td><td></td></tr></tbody></table>

### Trade

### Security Type: [TRADE](broken-reference)

Endpoints under **Trade** require an API Key and a signature

## &#x20;New Order

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/sapi/v1/order`

&#x20;**Rate Limit: 100times/2s**

#### Query Parameters

| Name        | Type    | Description  |
| ----------- | ------- | ------------ |
| X-CH-SIGN   | string  | Sign         |
| X-CH-APIKEY | string  | Your API-key |
| X-CH-TS     | integer | timestamp    |

#### Request Body

| Name                                     | Type    | Description                                                                   |
| ---------------------------------------- | ------- | ----------------------------------------------------------------------------- |
| symbol<mark style="color:red;">\*</mark> | String  | Symbol Name. E.g. `BTCUSDT`                                                   |
| symbolName                               | String  | Currency display name: choose either **symbol** or **symbolName** to fill in. |
| volume<mark style="color:red;">\*</mark> | number  | Order vol. For MARKET BUY orders, vol=amount.                                 |
| side<mark style="color:red;">\*</mark>   | String  | Side of the order,`BUY/SELL`                                                  |
| type<mark style="color:red;">\*</mark>   | String  | Type of the order, `LIMIT/MARKET`                                             |
| price<mark style="color:red;">\*</mark>  | number  | Order price, REQUIRED for LIMIT orders                                        |
| newClientOrderId                         | String  | Unique order ID generated by users to mark their orders                       |
| recvwindow                               | integer | Time window                                                                   |

{% tabs %}
{% tab title="200: OK  Successfully post new order" %}
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
{% endtab %}
{% endtabs %}

**weight(IP/UID): 5**

#### Response:

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>orderId</td><td>long</td><td><code>150695552109032492</code></td><td>ID of the order</td><td></td></tr><tr><td>clientorderId</td><td>string</td><td><code>213443</code></td><td>A unique ID of the order.</td><td></td></tr><tr><td>symbol</td><td>string</td><td><code>BTCUSDT</code></td><td>Symbol Name</td><td></td></tr><tr><td>transactTime</td><td>integer</td><td><code>1273774892913</code></td><td>Time the order is placed</td><td></td></tr><tr><td>price</td><td>float</td><td><code>4765.29</code></td><td>Time the order is placed</td><td></td></tr><tr><td>origQty</td><td>float</td><td><code>1.01</code></td><td>Quantity ordered</td><td></td></tr><tr><td>executedQty</td><td>float</td><td><code>1.01</code></td><td>Quantity of orders that has been executed</td><td></td></tr><tr><td>type</td><td>string</td><td><code>LIMIT</code></td><td>Order type <code>LIMIT,MARKET</code></td><td></td></tr><tr><td>side</td><td>string</td><td><code>BUY</code></td><td>Order side：<code>BUY, SELL</code></td><td></td></tr><tr><td>status</td><td>string</td><td><code>0</code></td><td>0 = new order</td><td></td></tr></tbody></table>

## &#x20;Test New Order

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/sapi/v1/order/test`

&#x20;Test new order creation and signature/recvWindow length. Creates and validates a new order but does not send the order into the matching engine.

#### Headers

| Name        | Type   | Description  |
| ----------- | ------ | ------------ |
| X-CH-APIKEY | String | Your API-key |
| X-CH-TS     | String | timestamp    |
| X-CH-SIGN   | String | Sign         |

#### Request Body

| Name                                     | Type    | Description                                             |
| ---------------------------------------- | ------- | ------------------------------------------------------- |
| type<mark style="color:red;">\*</mark>   | String  | Type of the order, `LIMIT/MARKET`                       |
| price<mark style="color:red;">\*</mark>  | number  | Order price, REQUIRED for `LIMIT` orders                |
| volume<mark style="color:red;">\*</mark> | number  | Order vol. For MARKET BUY orders, vol=amount.           |
| side<mark style="color:red;">\*</mark>   | String  | Side of the order, `BUY/SELL`                           |
| symbol<mark style="color:red;">\*</mark> | String  | Symbol Name. E.g. `BTCUSDT`                             |
| recvwindow                               | integer | Time window                                             |
| newClientorderId                         | String  | Unique order ID generated by users to mark their orders |

{% tabs %}
{% tab title="200: OK  Successfully test new order" %}
```javascript
{
    // Response
}
```
{% endtab %}
{% endtabs %}

**weight(IP/UID): 1**





## &#x20;Batch Orders

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/sapi/v1/batchOrders`

&#x20;**batch contains at most 10 orders**

#### Headers

| Name        | Type   | Description  |
| ----------- | ------ | ------------ |
| X-CH-APIKEY | String | Your API-key |
| X-CH-TS     | String | timestamp    |
| X-CH-SIGN   | String | Sign         |

#### Request Body

| Name                                     | Type   | Description                                                                        |
| ---------------------------------------- | ------ | ---------------------------------------------------------------------------------- |
| orders                                   | number | <p>The batch order information can contain a maximum of 10 records.</p><p><br></p> |
| symbol<mark style="color:red;">\*</mark> | String | Symbol Name. E.g. `BTCUSDT`                                                        |
| symbolName                               | String | Currency display name: choose either **symbol** or **symbolName** to fill in.      |

{% tabs %}
{% tab title="200: OK " %}
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
{% endtab %}
{% endtabs %}

**weight(IP/UID): 10**

#### Resquest `orders` field:

| name      | type   | Example        | Description |
| --------- | ------ | -------------- | ----------- |
| price     | folat  | 1000           | Price       |
| volume    | folat  | 20.1           | Quantity    |
| side      | String | BUY/SELL       | Direction   |
| batchType | String | `LIMIT/MARKET` | Type        |

#### Resquest <a href="#resquest-orders-field" id="resquest-orders-field"></a>

| idsString | String  | “3213213” | A collection of order numbers of type String. |
| --------- | ------- | --------- | --------------------------------------------- |
| ids       | integer | 2100      | Collection of order numbers.                  |





## &#x20;Query Order

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/order`

#### Query Parameters

| Name                                      | Type   | Description                                                                                      |
| ----------------------------------------- | ------ | ------------------------------------------------------------------------------------------------ |
| orderId<mark style="color:red;">\*</mark> | String | Order ID                                                                                         |
| newClientorderId                          | String | Client Order Id, Unique order ID generated by users to mark their orders. E.g. 354444heihieddada |
| symbol<mark style="color:red;">\*</mark>  | String | Symbol Name. E.g. `BTCUSDl`                                                                      |
| symbolName                                | String | Currency display name: choose either **symbol** or **symbolName** to fill in.                    |

#### Headers

| Name        | Type   | Description           |
| ----------- | ------ | --------------------- |
| X-CH-APIKEY | String | Your API-key          |
| X-CH-TS     | String | timestampResponses200 |
| X-CH-SIGN   | String | Sign                  |

{% tabs %}
{% tab title="200: OK " %}
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
{% endtab %}
{% endtabs %}

**weight(IP/UID): 1**

#### **Response:**

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>Example</th><th>Description</th><th></th></tr></thead><tbody><tr><td>orderId</td><td>long</td><td><code>150695552109032492</code></td><td>Order ID (system generated)</td><td></td></tr><tr><td>clientorderId</td><td>string</td><td><code>213443</code></td><td>Order ID (sent by yourself)</td><td></td></tr><tr><td>symbol</td><td>string</td><td><code>BTCUSDT</code></td><td>Currency Pair Name</td><td></td></tr><tr><td>price</td><td>float</td><td><code>4765.29</code></td><td>Order Price</td><td></td></tr><tr><td>origQty</td><td>float</td><td><code>1.01</code></td><td>Number of orders</td><td></td></tr><tr><td>executedQty</td><td>float</td><td><code>1.01</code></td><td>Number of orders already filled</td><td></td></tr><tr><td>avgPrice</td><td>float</td><td><code>4754.24</code></td><td>Average price of orders already filled</td><td></td></tr><tr><td>type</td><td>string</td><td>limit</td><td>The order type<code>LIMIT,MARKET</code></td><td></td></tr><tr><td>side</td><td>string</td><td><code>BUY</code></td><td>Order direction. Possible values can only be: BUY (buy long) and SELL (sell short)</td><td></td></tr><tr><td>status</td><td>string</td><td><code>NEW</code></td><td>Order status. Possible values are NEW (new order, no transaction), PARTIALLY_FILLED (partially filled), FILLED (fully filled), CANCELED (cancelled) and REJECTED (order rejected).POST</td><td></td></tr><tr><td>transactTime</td><td>string</td><td>1574327555669</td><td>Order Creation Time</td><td></td></tr></tbody></table>





## Cancel Order

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/sapi/v1/cancel`

#### Headers

| Name        | Type   | Description  |
| ----------- | ------ | ------------ |
| X-CH-APIKEY | String | Your API-key |
| X-CH-TS     | String | timestamp    |
| X-CH-SIGN   | String | Sign         |

#### Request Body

| Name                                      | Type   | Description                                                                                      |
| ----------------------------------------- | ------ | ------------------------------------------------------------------------------------------------ |
| newClientOrderId                          | String | Client Order Id, Unique order ID generated by users to mark their orders. E.g. 354444heihieddada |
| orderId<mark style="color:red;">\*</mark> | String | Order ID                                                                                         |
| symbol<mark style="color:red;">\*</mark>  | String | Symbol Name. E.g. `BTCUSDT`                                                                      |

{% tabs %}
{% tab title="200: OK " %}
```javascript
{
    'symbol': 'BHTUSDT', 
    'clientOrderId': '0', 
    'orderId': '499890200602846976', 
    'status': 'CANCELED'
}

```
{% endtab %}
{% endtabs %}

**weight(IP/UID): 5**

#### Response:

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>orderId</td><td>long</td><td><code>150695552109032492</code></td><td>ID of the order</td><td></td></tr><tr><td>clientorderId</td><td>string</td><td><code>213443</code></td><td>Unique ID of the order.</td><td></td></tr><tr><td>symbol</td><td>string</td><td><code>BTCUSDT</code></td><td>Name of the symbol</td><td></td></tr><tr><td>status</td><td>string</td><td><code>NEW</code></td><td>The state of the order.Possible values include <code>NEW</code>, <code>PARTIALLY_FILLED</code>, <code>FILLED</code>, <code>CANCELED</code>, and <code>REJECTED</code>.POST<br></td><td></td></tr></tbody></table>





## &#x20;Batch cancel orders

<mark style="color:green;">`POST`</mark> `https://openapi.xxx.xx/sapi/v1/batchCancel`

&#x20;**batch contains at most 10 orders**

#### Headers

| Name        | Type   | Description  |
| ----------- | ------ | ------------ |
| X-CH-APIKEY | String | Your API-key |
| X-CH-TS     | String | timestamp    |
| X-CH-SIGN   | String | Sign         |

#### Request Body

| Name                                     | Type   | Description                                    |
| ---------------------------------------- | ------ | ---------------------------------------------- |
| orderIds                                 | String | Order ID collection `[123,456]`Responses200GET |
| symbol<mark style="color:red;">\*</mark> | String | Symbol Name. E.g. `BTCUSDT`                    |

{% tabs %}
{% tab title="200: OK " %}
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
{% endtab %}
{% endtabs %}

**weight(IP/UID): 10**

## &#x20;Current Open Orders

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/openOrders`

#### Query Parameters

| Name                                     | Type   | Description                 |
| ---------------------------------------- | ------ | --------------------------- |
| symbol<mark style="color:red;">\*</mark> | String | Symbol Name. E.g. `BTCUSDT` |
| limit                                    | String | Default 100; Max 1000       |

#### Headers

| Name        | Type   | Description  |
| ----------- | ------ | ------------ |
| X-CH-APIKEY | String | Your API-key |
| X-CH-TS     | String | timestamp    |
| X-CH-SIGN   | String | Sign         |

{% tabs %}
{% tab title="200: OK " %}
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
{% endtab %}
{% endtabs %}

**weight(IP/UID): 1**

#### **Response:**

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th><th></th></tr></thead><tbody><tr><td>orderId</td><td>long</td><td><code>150695552109032492</code></td><td>ID of the order</td><td></td></tr><tr><td>orderIdString</td><td>string</td><td>"<code>150695552109032492"</code></td><td>Character String Type Order ID (Recommended)</td><td></td></tr><tr><td>clientorderId</td><td>string</td><td><code>213443</code></td><td>Unique ID of the order.</td><td></td></tr><tr><td>symbol</td><td>string</td><td><code>BTCUSDT</code></td><td>Name of the symbol</td><td></td></tr><tr><td>price</td><td>float</td><td><code>4765.29</code></td><td>Price of the order</td><td></td></tr><tr><td>origQty</td><td>float</td><td><code>1.01</code></td><td>Quantity ordered</td><td></td></tr><tr><td>executedQty</td><td>float</td><td><code>1.01</code></td><td>Quantity of orders that has been executed</td><td></td></tr><tr><td>avgPrice</td><td>float</td><td><code>4754.24</code></td><td>Average price of filled orders.</td><td></td></tr><tr><td>type</td><td>string</td><td><code>LIMIT</code></td><td>The order type<code>LIMIT,MARKET</code></td><td></td></tr><tr><td>side</td><td>string</td><td><code>BUY</code></td><td>The order side <code>BUY,SELL</code></td><td></td></tr><tr><td>status</td><td>string</td><td><code>NEW</code></td><td>The state of the order.Possible values include <code>NEW</code>, <code>PARTIALLY_FILLED</code>, <code>FILLED</code>, <code>CANCELED</code>, and <code>REJECTED</code>.GET</td><td></td></tr><tr><td>time</td><td>string</td><td>1574327555669</td><td>Creation Time</td><td></td></tr></tbody></table>



## Trades

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/myTrades`

#### Query Parameters

| Name                                     | Type   | Description                 |
| ---------------------------------------- | ------ | --------------------------- |
| symbol<mark style="color:red;">\*</mark> | String | Symbol Name. E.g. `BTCUSDT` |
| limit                                    | String | Default 100; Max1000        |
| fromId                                   | String | Trade Id to fetch from      |

#### Headers

| Name        | Type   | Description  |
| ----------- | ------ | ------------ |
| X-CH-APIKEY | String | Your API-key |
| X-CH-TS     | String | timestamp    |
| X-CH-SIGN   | String | Sign         |

{% tabs %}
{% tab title="200: OK " %}
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
{% endtab %}
{% endtabs %}

**weight(IP/UID): 1**

#### **Response:**

<table data-header-hidden><thead><tr><th>name</th><th width="150">type</th><th>example</th><th>description</th></tr></thead><tbody><tr><td>symbol</td><td>string</td><td><code>BTCUSDT</code></td><td>Name of the symbol</td></tr><tr><td>id</td><td>integer</td><td><code>28457</code></td><td>Trade ID</td></tr><tr><td>bidId</td><td>long</td><td><code>150695552109032492</code></td><td>Bid Order ID</td></tr><tr><td>askId</td><td>long</td><td><code>150695552109032492</code></td><td>Ask Order ID</td></tr><tr><td>price</td><td>integer</td><td><code>4.01</code></td><td>Price of the trade</td></tr><tr><td>qty</td><td>float</td><td><code>12</code></td><td>Quantiry of the trade</td></tr><tr><td>time</td><td>number</td><td><code>1499865549590</code></td><td>timestamp of the trade</td></tr><tr><td>isBuyer</td><td>bool</td><td><code>true</code></td><td><code>true</code>= Buyer <code>false</code>= Seller</td></tr><tr><td>isMaker</td><td>bool</td><td><code>false</code></td><td><code>true</code>=Maker <code>false</code>=Taker</td></tr><tr><td>feeCoin</td><td>string</td><td><code>ETH</code></td><td>Trading fee coin</td></tr><tr><td>fee</td><td>number</td><td><code>0.001</code></td><td>Trading fee</td></tr><tr><td>bidUserId</td><td>long</td><td>23334</td><td>Buyer UID</td></tr><tr><td>askUserId</td><td>long</td><td>44112</td><td>Seller UID</td></tr><tr><td>isSelf</td><td>bool</td><td>true</td><td>whether is self dealt</td></tr></tbody></table>



## Account

### Security Type: USER\_DATA

Endpoints under Account require an API-key and a signature.\


## &#x20;Account Information

<mark style="color:blue;">`GET`</mark> `https://openapi.xxx.xx/sapi/v1/account`

#### Headers

| Name        | Type   | Description  |
| ----------- | ------ | ------------ |
| X-CH-APIKEY | String | Your API-key |
| X-CH-TS     | String | timestamp    |
| X-CH-SIGN   | String | Sign         |

{% tabs %}
{% tab title="200: OK  Successfully retrieved account information." %}
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
{% endtab %}
{% endtabs %}

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
