# Capture
The Capture and Force Capture transactions are a capture of a previous pre-authorization. A capture can be done on the amount equal to or less than the dollar amount of the referenced pre-authorization.

```json
/sale/{bric}/capture
```
**Method:**
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

**Capture Example**
```json
{
"accountNumber": "4111111111111111",
 "amount": "127.99",
 "TransactionId": 123
}
```
