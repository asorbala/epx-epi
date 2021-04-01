# Sale

The Sale transaction is an authorization and a capture within the same transaction, provided the authorization portion is approved and is otherwise able to settle. When a sale transaction is run against an account number, the authorization occurs for the dollar amount in the transaction. Imidiately after, the capture automatically occurs so that it will settle during the next settlement window.

The sale transaction in JSON appears as one of the two examples below:

- **POST** `/sale`
- **POST** `/sale/{bric}`

### Sale Examples:

* * *

#### Sale Example – Simple Authorization (Auth) and Capture

**Endpoint:**
```
/sale
```
**Method**: 

```json
POST
```

The above request requires an **account number**, **amount**, and **transaction number**.

```json
{
 "accountNumber": "4111111111111111",
 "amount": "127.99",
 "TransactionId": 123
}
```
**Required HTTP Headers**

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload|

For more hearders navigate [here](url)


* * *

### Sale Example – Sale Auth with BRIC

If a bric storage transaction was done previously, use the existing bric to create a new
transaction.

```json
/sale/0123456789012345678
```

**Method:** 

```json
POST
```

Only the amount is required:

```json
{
 "amount": "127.99"
}
```

* * *

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
