# Incremental Auth
To add an additional amount of money to a transaction, or incrementally authorize a new
amount, the original transaction BRIC is required. The amount in the json example below is the additional amount needed.

For example, if the initial authorization was $20 and the new amount needs to be $30, the json payload would show an Amount of 10.

```json
/sale/inc/<BRIC>
```

**Method**: 
```json
PUT
```
**Required HTTP Headers**

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload|

For more hearders navigate [here](url)

**JSON Playload:**
```json
{
"amount": 10,
"transaction": 123
}
```
---
### Response
The response from a /sale transaction will be the same regardless of additional fields included in the request.

```json
{
"data": {
 "authorization": "009835",
 "response": "00",
 "text": "APPROVAL 009835"
},
"errors": null,
"reference": {
 "bric": "00DGZ9BTJB05MDGU002",
 "timestamp": "2019-05-21T19:38:02Z"
}
```

