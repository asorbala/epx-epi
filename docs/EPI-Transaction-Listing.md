# Transaction Listing

The `/sale` endpoint provides the ability to get a list of transactions based on the `four part key`.
When called directly, it will list all transactions specific to that four part key at the terminal level.
If the detail property is set to `dba`, it will tell the endpoint to return all transactions at the DBA
level, essentially using the first three parts of the four part key.

**Endpoint Example:**
```json
/sale
/sale?detail=dba
```

**Method:**
```json
GET
```

**Required HTTP Headers**

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload|

For more hearders navigate [here](url)

**Transaction Lookup Example Response**
```json
{
"data": {
 "rowCount": "3",
 "rows": [
 {
 "authamount": "5.25",
 "authbric": "03QH1K6D8LFNJ4F2YNT",
 "authtrandategmt": "26-Jul-2019",
 "epxid/customer": "9001",
 "epxid/dba": "361",
 "epxid/merchant": "2626",
 "epxid/terminal": "5",
 "system/trantype": "CCR2",
 "void": "Y"
 },
 {
 "authamount": "5.25",
 "authbric": "03QH1K6GWEZ3YN53YY0",
 "authtrandategmt": "26-Jul-2019",
 "epxid/customer": "9001",
 "epxid/dba": "361",
 "epxid/merchant": "2626",
 "epxid/terminal": "5",
 "system/trantype": "CCR2",
 "void": "N"
 },
 {
 "authamount": "5.25",
 "authbric": "03QH1K6GZ6VTFNEAYY1",
 "authtrandategmt": "26-Jul-2019",
 "epxid/customer": "9001",
 "epxid/dba": "361",
 "epxid/merchant": "2626",
 "epxid/terminal": "5",
 "system/trantype": "CCR2",
 "void": "Y"
 }
 ]
},
"errors": null,
"reference": {
 "bric": "00DH2YD4RN57P04P0D2",
 "timestamp": "2019-08-09T22:22:13Z"
}
}
```
