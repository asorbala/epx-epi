# Sale Edit (Tip Adjust)

The Edit Authorization and Capture transaction is used to edit an open Sale (Authorization and Capture) transaction. The transaction is a BRIC-based request and can only be performed on an approved Sale transaction that has not been voided, closed, or settled.

```json
/sale/0123456789012345678
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
"amount": 131.99,
"tipAmount": 5.55
}
```

---
## Response
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