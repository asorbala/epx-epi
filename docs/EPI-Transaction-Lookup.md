# Lookup

The /sale endpoint provides the ability to get the details for a single transaction based on the BRIC (EPX Transaction Identifier) value.



**Sale Lookup Endpoint:**
```json
/sale/{bric}
```
**Refund Lookup Endpoint:**
```json
/refund/{bric}
```

**Method:**
```json
GET
```

**Required HTTP Headers:**

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload|

For more hearders navigate [here](url)

**Sale Lookup Example**

```json
/sale/0123456789012345678
```

**Sale Lookup Example Response**
```json
{
"data": {
 "authamount": "99.00",
 "authorization": "000401",
 "authtrandategmt": "08-Aug-2019",
 "batchid": "1829",
 "closeddate": "09-Aug-2019",
 "epxid/customer": "9001",
 "epxid/dba": "361",
 "epxid/merchant": "2626",
 "epxid/terminal": "5",
 "folionumber": "",
 "invoicenumber": "ABC-123",
 "markedtosettle": "N",
 "ordernumber": "",
 "referencenumber": "",
 "rentalnumber": "",
 "response": "00",
 "system/trantype": "CCE1",
 "tipamount": "0.00",
 "transaction": "217",
 "userdata/1": "",
 "userdata/10": "",
 "userdata/2": "",
 "userdata/3": "",
 "userdata/4": "",
 "userdata/5": "",
 "userdata/6": "",
 "userdata/7": "",
 "userdata/8": "",
 "userdata/9": "",
 "void": "N"
},
"errors": null,
"reference": {
 "bric": "00DH2YW7A8K7K0ZL0D1",
 "timestamp": "2019-08-09T22:06:05Z"
}
}
```
