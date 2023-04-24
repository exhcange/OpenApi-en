# Withdraw

{% swagger method="post" path="/sapi/v1/withdraw/apply" baseUrl="https://openapi.xxx.com" summary="Apply for withdrawal" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-APIKEY" required="true" type="String" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" required="true" type="String" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" required="true" type="Integer" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" %}
currency name，For coins that support multiple mainchains, the actual currency name needs to be transmitted, as shown in 

[Appendix 1](appendix-1.md)


{% endswagger-parameter %}

{% swagger-parameter in="body" name="withdrawOrderId" required="true" type="String" %}
Custom withdrawal id, guaranteed to be unique
{% endswagger-parameter %}

{% swagger-parameter in="body" name="amount" required="true" type="String" %}
quantity
{% endswagger-parameter %}

{% swagger-parameter in="body" name="address" required="true" type="String" %}
Withdrawal address
{% endswagger-parameter %}

{% swagger-parameter in="body" name="label" type="String" %}
Some currencies such as XRP, XMR allow filling of secondary address labels
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```json
{
    "code":"Ѳ",//Return code, 0 for success, other failures
    "msg":"sucess",//returned messages
    "data":{
        "id":518353 //Platform withdrawal id
    }
}
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 100**

{% swagger method="post" path="/sapi/v1/withdraw/query" baseUrl="https://openapi.xxx.com" summary="Withdrawal record query" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="X-CH-APIKEY" required="true" type="String" %}
Your API-key
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-SIGN" required="true" type="String" %}
Sign
{% endswagger-parameter %}

{% swagger-parameter in="header" name="X-CH-TS" required="true" type="String" %}
timestamp
{% endswagger-parameter %}

{% swagger-parameter in="body" name="symbol" type="String" %}
Currency Name, For coins that support multiple mainchains, the actual currency name needs to be transmitted, as shown in 

[Appendix 1](appendix-1.md)


{% endswagger-parameter %}

{% swagger-parameter in="body" name="withdrawId" type="String" %}
Platform withdrawal id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="withdrawOrderId" type="String" %}
Custom withdrawal id
{% endswagger-parameter %}

{% swagger-parameter in="body" name="startTime" type="String" %}
Start time, timestamp, default 90 days ago
{% endswagger-parameter %}

{% swagger-parameter in="body" name="endTime" type="String" %}
end time, timestamp, default current time
{% endswagger-parameter %}

{% swagger-parameter in="body" name="page" type="String" %}
Page number, starting at 1
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```json
{
    "code": "0",
    "msg": "成功",
    "data": {
        "withdrawList": [
            {
                "symbol": "TUSDT",
                "amount": 19.99999,
                "address": "TFFrjNfBAagmFWypE3Hnv6zPKAFhd3VcDf",
                "withdrawOrderId": "abc123",
                "fee": 0.00001,
                "ctime": 1605585397000,
                "txId": "749864_20201117115930",
                "id": 749864,
                "applyTime": 1666754820000,
                "status": 5,
                "info": ""
            },
            {
                "symbol": "TUSDT",
                "amount": 10.50999,
                "address": "TYsTiVVDU5VmnUPufzGD52CD1hSbPATT3Q",
                "withdrawOrderId": "abc456",
                "fee": 0.00001,
                "ctime": 1607089149000,
                "txId": "764294_20201204094130",
                "id": 764294,
                "applyTime": 1666754820000",
                "status": 5,
                "info": ""
            }
        ],
        "count": 2
    }
}
```
{% endswagger-response %}
{% endswagger %}

**weight(IP/UID): 100**

#### Responses

| Parameter       | Type   | Example                            | Remark                                                                                                                |
| --------------- | ------ | ---------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| symbol          | String | USDT                               | Withdrawal currency                                                                                                   |
| amount          | Number | 9.99                               | quantity                                                                                                              |
| address         | String | TFFrjNfBAagmFWypE3Hnv6zPKAFhd3VcDf | Withdrawal address                                                                                                    |
| withdrawOrderId | String | abc123                             | Custom withdrawal id                                                                                                  |
| fee             | Number | 0.01                               | fee                                                                                                                   |
| ctime           | Number | 1605585397000                      | creation time                                                                                                         |
| txId            | String | 749864\_20201117115930             | Withdrawal transaction id                                                                                             |
| id              | Number | 749864                             | Platform withdrawal id                                                                                                |
| applyTime       | Number | 1605585397000                      | On-chain time                                                                                                         |
| status          | Number | 2                                  | Withdrawal status, 0-unapproved, 1-approved, 2-approved rejected, 3-payment, 4-payment failed, 5-completed, 6-revoked |
| info            | String | Withdrawal address error           | Review rejection reasons                                                                                              |
