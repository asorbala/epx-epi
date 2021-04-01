# Force Capture
**Method:**
```json
POST 
```

```json
/sale/capture
/sale/capture/{bric}
```
**Required HTTP Headers**

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload|

For more hearders navigate [here](url)

### Force Capture Example 1
```json
/sale/capture
```
```json
{
 "accountNumber": "4111111111111111",
 "amount": "127.99",
 "TransactionId": 123
}
```

### Force Capture Example 2
This example uses a bric for a force capture:
```json
/sale/capture/0123456789012345678
```
```json
{
 "amount": "127.99",
 "TransactionId": 123
}
```

