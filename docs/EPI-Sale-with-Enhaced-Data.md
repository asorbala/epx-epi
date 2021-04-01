# Sale with Enhanced and Optional Data

This example includes the use of the optional user data fields “userData” and “special” as well as enhanced data. The enhanced data in the example is passed in an array to handle multiple line items. Each line is designated by a line number in the definition. The remaining field numbers represent the specific data required for the “datatype” as defined in the card specification.

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
"account": "4111111111111111",
"amount": 127.99,
"transaction": 123,
"invoiceNumber": "ABC-123",
"tlvSets": "0123 000007LODGING005005QUEEN0090012018006120119020002BC055013BRIAN
JOHNSON05600320102300589.540240049.23028006103.2305300543.00",
"userData": {
 "1": "Mobile Payment",
 "3": "Off Peak Measurement"
},
"special": {
 "2": "soloar",
 "4": "regen"
}
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

### Enhanced Data (TLV Data)
More information about the enhanced data can be found [here](url)