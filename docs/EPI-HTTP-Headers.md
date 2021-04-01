# HTTP Headers and Response Codes

### Required HTTP Headers

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload|

### Optional HTTP Headers

|Name| Value |Description|
|---|---|---|
|EPI-Trace| User defined | - Optional value that can be sent in with the request and will be echoed back with response. <br> - Can be used as unique value to help identify transactions from merchant perspective. <br> - Value is not persisted with transaction and is only good during the current request / response chain.|

### CRUD Matrix

|Operation|HTTP Verb| Result| Example| Example Note|
|---|---|---|---|---|
|Create| POST| New record |/sale| Details will be in JSON|
|Read| GET| Read record(s)|/batch/123| Returns back JSON array of records|
|Update| PUT| Update record(s)|/void/0123456789012345678| Updates a record|
|Delete| DELETE| Remove record(s)|Unused| Unused|

### Common HTTP Response Codes
EPI uses HTTP response codes to indicate the success or failure of a request.

|Code| Description|
|---|---|
|200 OK| Request was successful|
|400 Bad Request| Bad request|
|401 Unauthorized| EPIKey is required|
|403 Forbidden| EPIKey provided doesn’t have the right to perform the request|
|404 Not Found| Requested resource was not found|
|405 Method Not Allowed| HTTP method request is not allowed|
|500 Internal Server Error| Unexpected server error has occurred|