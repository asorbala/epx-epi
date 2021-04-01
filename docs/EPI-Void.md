# Void

The Void transaction is used to stop a sale, capture, or refund transaction prior to settlement. If the transaction has already been settled, this function will no longer be available.

**Method:**
```json
PUT
```

**Endpoint:**
```json
/void/{bric}
```

**Required HTTP Headers**

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload|

For more hearders navigate [here](url)

### Void Example:

This example requires a bric in the URL
```json
/void/0123456789012345678
```