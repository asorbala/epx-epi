# Authorization (Auth only)

For an authorize only (no capture), include the capture flag and set it to false.
All authorize only transactions will need to be individually Captured at a later time to settle during the next settlement window.

**Note:** Capture flag default set to `true`.

**Endpoint Example:**
```json
/sale
```
**Method:** 
```json
POST
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
 "accountNumber": "4111111111111111",
 "amount": "127.99",
 "capture": false,
 "TransactionId": 123
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


