# Reverse
The Reverse transaction is used to reverse the authorization of funds on a credit card. This will release the funds that are being held at the issuing bank.

**Endpoint:**
```json
/reverse/{bric}
```
**Method:**
```json
POST
```
**Request Body:**
```json
{
 "batchId": 123,
 "transactionId": 123
}
```
**Required HTTP Headers**

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload|

For more hearders navigate [here](url)

#### Reverse Example
```json
/reverse/0123456789012345678
```

```json
{
 "batchId": 123,
 "transactionId": 123
}
```

#### Example Response
```json
{
 "data": null,
 "errors": null,
 "reference": {
 "bric": "0123456789012345678",
 "timestamp": "2019-05-05T20:53:41Z"
 }
}
```

