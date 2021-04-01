# Refund

The Refund transaction is a transaction used to return funds to an account previously acted upon by a sale or capture transaction. A single refund for the full amount of the original transaction, or numerous partial refunds can be performed with dollar amounts less than and not to exceed the total amount of the original sale or capture being acted upon.


## Linked Refund
---

Linked Refund requests require the bric in the URL:

**Method:**
```json
POST
```

**Endpoint:**
 ```json
/refund/{bric}
```

**Required HTTP Headers**

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload|

For more hearders navigate [here](url)

**Endpoint Example:**

```json
/refund/0123456789012345678
```

**Playload example:**
```json
{
 "amount": "127.99",
 "TransactionId": 123
}
```

## Unlinked Refund
This example requires an account number, amount, and transaction number in the payload.

**Method:**
```json
POST
```

**Endpoint:**
 ```json
/refund/{bric}
```

**Required HTTP Headers**

|Name| Value |Description|
|---|---|---|
|Content-Type| Application/json| Content type of message. For most messages, this will be the default.|
|EPI-Id| 111-222-333-444| Merchant four-part key|
|EPI-Signature| 0123456789ABCDEF| HMAC of URL and payload
For more hearders navigate [here](url)

**Endpoint Example:**
```json
/refund
```

**Playload example:**
```json
{
 "accountNumber": "4111111111111111",
 "amount": "127.99",
 "TransactionId": 123
}
```

## Refund Lookup
---
```json
GET /refund/{bric}
```






