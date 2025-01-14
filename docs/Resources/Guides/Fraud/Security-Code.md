---
tags: [carat, commerce-hub, card-not-present, security-code, fraud, security-code-verification]
---


# Security Code

## Overview
Commerce Hub supports [security code](?path=docs/Resources/FAQs-Glossary/Glossary.md#security-code) verification, a service where cardholder is prompted to enter the 3 or 4-digit security code to have it verified by the association bank. Security code verification can be used as a [fraud prevention](?path=docs/Resources/Guides/Fraud/Fraud-Settings-AVS-CVV.md) measure in card not present transaction.

---

## Requirements

For the transactions where security code verification is required, the merchant's API is required to pass `securityCode` and `securityCodeIndicator` as part of the card array.

#### Component: card

| Variable | Type| Maximum Length | Description/Values|
|---------|----------|----------------|---------|
|`securityCode` | *string* | 3| The card security code.|
|`securityCodeIndicator` | *string* | | Indicates how the security code is passed. **Valid Values:** NOT_SUPPORTED (Default), PROVIDED, VALUE_ILLEGIBLE,  NOT_AVAILABLE.|

---

## Verification Request

### Endpoint

<!-- theme: success -->
>**POST** `/payments-vas/v1/accounts/verification`

### Payload Example

<!--
type: tab
title: Request
-->

##### Example of a security code verification request.

```json
{
   "source":{
      "sourceType":"PaymentCard",
      "card":{
         "cardData":"4005550000000019",
         "expirationMonth":"02",
         "expirationYear":"2035",
         "securityCode":"123",
         "securityCodeIndicator":"PROVIDED"
      }
}

```
<!--
type: tab
title: Response
-->

##### Example of a security code verification response.

```json
{
   "gatewayResponse":{
      "orderId":"R-3b83fca8-2f9c-4364-86ae-12c91f1fcf16",
      "transactionType":"token",
      "transactionState":"authorized",
      "transactionOrigin":"ecom",
      "transactionProcessingDetails":{
         "transactionDate":"2016-04-16",
         "transactionTime":"2016-04-16T16:06:05Z",
         "apiTraceId":"rrt-0bd552c12342d3448-b-ea-1142-12938318-7",
         "clientRequestId":"30dd879c-ee2f-11db-8314-0800200c9a66",
         "transactionId":"838916029301"
      }
   },
   "paymentSource":{
      "sourceType":"PaymentCard",
      "tokenData":"1234123412340019",
      "PARId":"string",
      "declineDuplicates":"FALSE",
      "tokenSource":"string",
      "card":{
         "nameOnCard":"Jane Smith",
         "expirationMonth":"05",
         "expirationYear":"2025",
         "bin":"400555",
         "last4":"0019",
         "scheme":"VISA"
      }
   },
   "processorResponseDetails":{
      "approvalStatus":"APPROVED",
      "approvalCode":"OK3483",
      "referenceNumber":"845366457890-TODO",
      "schemeTransactionId":"019078743804756",
      "feeProgramIndicator":"string",
      "processor":"fiserv",
      "responseCode":"00",
      "responseMessage":"APPROVAL",
      "hostResponseCode":"54022",
      "hostResponseMessage":"",
      "localTimestamp":"2016-04-16T16:06:05Z",
      "bankAssociationDetails":{
         "associationResponseCode":"000",
         "transactionTimestamp":"2016-04-16T16:06:05Z",
         "avsSecurityCodeResponse":{
            "securityCodeMatch":"MATCH",
            "association":{
               "securityCodeResponse":"MATCH"
            }
         }
      }
   }
}
```

<!-- type: tab-end -->

---

## Verification with Charges Request

### Endpoint

<!-- theme: success -->
>**POST** `/payments/v1/charges`

### Payload Example

<!--
type: tab
title: Request
-->

##### Example of a security code verification during a charges request.

```json
{
   "amount":{
      "total":"12.04",
      "currency":"USD"
   },
   "source":{
      "sourceType":"PaymentCard",
      "card":{
         "cardData":"4005550000000019",
         "expirationMonth":"02",
         "expirationYear":"2035",
         "securityCode":"123",
         "securityCodeIndicator":"PROVIDED"
      }
   },
   "transactionDetails":{
      "captureFlag":true
   }
}

```
<!--
type: tab
title: Response
-->

##### Charges response containing security code response details.

```json
{
   "gatewayResponse":{
      "orderId":"R-3b83fca8-2f9c-4364-86ae-12c91f1fcf16",
      "transactionType":"token",
      "transactionState":"authorized",
      "transactionOrigin":"ecom",
      "transactionProcessingDetails":{
         "transactionDate":"2016-04-16",
         "transactionTime":"2016-04-16T16:06:05Z",
         "apiTraceId":"rrt-0bd552c12342d3448-b-ea-1142-12938318-7",
         "clientRequestId":"30dd879c-ee2f-11db-8314-0800200c9a66",
         "transactionId":"838916029301"
      }
   },
   "paymentSource":{
      "sourceType":"PaymentCard",
      "tokenData":"1234123412340019",
      "PARId":"string",
      "declineDuplicates":"FALSE",
      "tokenSource":"string",
      "card":{
         "nameOnCard":"Jane Smith",
         "expirationMonth":"05",
         "expirationYear":"2025",
         "bin":"400555",
         "last4":"0019",
         "scheme":"VISA"
      }
   },
   "processorResponseDetails":{
      "approvalStatus":"APPROVED",
      "approvalCode":"OK3483",
      "referenceNumber":"845366457890-TODO",
      "schemeTransactionId":"019078743804756",
      "feeProgramIndicator":"string",
      "processor":"fiserv",
      "responseCode":"00",
      "responseMessage":"APPROVAL",
      "hostResponseCode":"54022",
      "hostResponseMessage":"",
      "localTimestamp":"2016-04-16T16:06:05Z",
      "bankAssociationDetails":{
         "associationResponseCode":"000",
         "transactionTimestamp":"2016-04-16T16:06:05Z",
         "avsSecurityCodeResponse":{
            "securityCodeMatch":"MATCH",
            "association":{
               "securityCodeResponse":"MATCH"
            }
         }
      }
   }
}
```

<!-- type: tab-end -->

---

## Response Values

The result of checking the cardholder’s entered security code against the Issuer’s system of record is is received in the response. The [processor response details](?path=docs/Resources/Master-Data/Processor-Response-Details.md) contains the security code response from the bank.

| Value | Description |
| ------- | ------- |
| MATCH | Security code matched. |
| NO_MATCH | Security code did not matched. |
| NOT_PROVIDED | Security code value was not provided. |
| NOT_PROCESSED | Security code verification was not processed. |
| NO_PARTICIPANT | Bank Associatino does not participate in security verification. |
| UNKNOWN | Unknown status. |

---

## See Also

- [API Explorer](../api/?type=post&path=/payments-vas/v1/accounts/verification)
- [Address/Security Code Filters](?path=docs/Resources/Guides/Fraud/Fraud-Settings-AVS-CVV.md)
- [Charges Request](?path=docs/Resources/API-Documents/Payments/Charges.md)
- [Card Details](?path=docs/Resources/Master-Data/Card.md)
- [Fraud Detect](?path=docs/Resources/Guides/Fraud/Fraud-Detect.md)
- [Fraud Filters](?path=docs/Resources/Guides/Fraud/Fraud-Settings-Filters.md)
- [Payment Card](?path=docs/Resources/Guides/Payment-Sources/Payment-Card.md)
- [Prepaid Gift Card](?path=docs/Resources/Guides/Payment-Sources/Gift-Card.md)
Fraud-Settings-Restrictions.md)
- [Processor Response Details](?path=docs/Resources/Master-Data/Processor-Response-Details.md)
- [Velocity Controls](?path=docs/Resources/Guides/Fraud/Fraud-Settings-Velocity.md)
- [Verification Request](?path=docs/Resources/API-Documents/Payments_VAS/Verification.md)

---
