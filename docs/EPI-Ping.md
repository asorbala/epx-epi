# Ping

**Method:**
```json
GET
``` 
**Endpoint:**
```json
/ping
```

**Required HTTP Headers**

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload|

For more hearders navigate [here](url)

**Ping Example**
```json
/ping
```
**Response**
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