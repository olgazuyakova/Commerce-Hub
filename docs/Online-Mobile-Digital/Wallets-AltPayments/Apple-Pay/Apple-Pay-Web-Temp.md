---
tags: [carat, commerce-hub, apple-pay, wallet, apple-pay-web-integration]
---

# Apple Pay: Web Integration


## Step 1: Create Merchant Identifier

First [create a merchant identifier](https://help.apple.com/developer-account/#/devb2e62b839?sub=dev103e030bb) in your developer account that uniquely identifies you to Apple Pay as a merchant who is able to accept payments. You can use the same merchant identifier for multiple native and web apps. The merchant identifier never expires.


<!-- theme: warning -->
>
> After Merchant Identifier is created, you will need us to generate the certificate for you using the Merchant Identifier. Please contact our Account Representative in order to get the certificate.

---

## Step 2: Create Payment Processing Certificate

Next [create a payment processing certificate](https://help.apple.com/developer-account/#/devb2e62b839?sub=devf31990e3f) that is associated with your merchant identifier and used to encrypt payment information. The payment processing certificate expires every 25 months and can be revoked. When that happens, just re-create the payment process certificate.

---


## Step 3: Register and Validate Merchant Account

Then [register the merchant](https://help.apple.com/developer-account/#/dev1731126fb) domains in your organization that will process the Apple Pay transactions and create a merchant identity certificate that you’ll use to authenticate communication with the Apple Pay servers.

---

## Step 4: Create Merchant Identity Certificate

[Create a merchant identity certificate](https://help.apple.com/developer-account/#/dev1731126fb?sub=dev17ad0bdc0) is required to authenticate communication with the Apple Pay servers.

---

## Step 5: Support Apple Pay on Website

Merchant can start supporting Apple Pay on their website either by using Commerce Hub's RESTful API with [Apple Pay's JS API Framework](https://developer.apple.com/documentation/apple_pay_on_the_web/apple_pay_js_api) or by using Commerce Hub Hosted Payment Page.

---

## Step 6: Presenting the Payment Sheet

A merchant can enhance the purchase experience from their website by creating a streamlined checkout process and presenting a customized Apple Pay payment sheet that allows customers to promptly authorize a payment and complete their transaction. Refer to Apple's website on how to customize the [payment sheet](https://developer.apple.com/design/human-interface-guidelines/apple-pay/overview/checkout-and-payment/#customize-the-payment-sheet).

---

## Step 7: Submit a Payment Request

<!--theme: warning-->
> This step is only required when utilizing Commerce Hub's RESTful API and Apple Pay JS. Hosted Checkout will manage the payment information automatically.

<!--
type: tab
title: Request
-->

##### Example of a Charge Payload Request.
```json
{
   "amount":{
      "total":"12.04",
      "currency":"USD"
   },
   "source":{
      "sourceType":"ApplePay",
      "data":"hbreWcQg980mUoUCfuCoripnHO210lvtizOFLV6PTw1DjooSwik778bH....",
      "header":{
        "applicationDataHash":"94ee059335e587e501cc4bf90613e0814f00a7b08bc7c648fd865a2af6a22cc2",
        "ephemeralPublicKey":"MFkwEwYHKoZIzj0CAQYIKoZIzj0DAQcDQgAEvR....",
        "publicKeyHash":"KRsyW0NauLpN8OwKr+yeu4jl6APbgW05/TYo5eGW0bQ=",
        "transactionId":"31323334353637"
      },
      "signature":"MIAGCSqGSIb3DQEHAqCAMIACAQExDzANBglghkgBZQMEAgEFADCABgkqhki.....",
      "version":"EC_v1",
      "applicationData":"VEVTVA==",
      "merchantId":"merchant.com.fapi.tcoe.applepay",
      "merchantPrivateKey":"MHcCAQEE234234234opsmasdsalsamdsad/asdsad/asdasd/....."
   },
   "transactionDetails":{
      "captureFlag":true,
      "createToken":true,
      "tokenProvider":"RSA"
   }
}

```

<!--
type: tab
title: Response
-->

##### Example of a Charge (201: Created) Response.

<!-- theme: info -->
> See [Error Responses](url) for additional examples.
```json
{
   "gatewayResponse":{
      "orderId":"R-3b83fca8-2f9c-4364-86ae-12c91f1fcf16",
      "transactionType":"charge",
      "transactionState":"authorized",
      "transactionOrigin":"ecom"
   },
   "transactionProcessingDetails":{
      "transactionDate":"2021-04-16",
      "transactionTime":"2021-04-16T16:06:05Z",
      "apiTraceId":"rrt-0bd552c12342d3448-b-ea-1142-12938318-7",
      "clientRequestId":"30dd879c-ee2f-11db-8314-0800200c9a66",
      "transactionId":"838916029301"
   },
   "source":"ApplePay",
   "paymentToken":{
      "tokenData":"1234123412340019",
      "PARId":"string",
      "declineDuplicates":false,
      "tokenSource":"RSA"
   },
   "paymentReceipt":{
      "approvedAmount":{
         "total":"1.00",
         "currency":"USD"
      },
      "processorResponseDetails":null,
      "approvalStatus":"APPROVED",
      "approvalCode":"OK7118",
      "referenceNumber":"845366457890-TODO",
      "schemeTransactionID":"019078743804756",
      "processor":"fiserv",
      "responseCode":"00",
      "responseMessage":"APPROVAL",
      "hostResponseCode":"54022",
      "hostResponseMessage":"Approved",
      "localTimestamp":"2021-04-16T16:06:05Z",
      "bankAssociationDetails":{
         "associationResponseCode":"000",
         "transactionTimestamp":"2021-04-16T16:06:05Z",
         "transactionReferenceInformation":null
      }
   }
}
```

<!-- type: tab-end -->

## See Also

- [API Explorer](url)
- [Apple Pay App Integration](Apple-Pay-App.md)
- [Charges](../../../Resources/API-Documents/Payments/Charges.md)
- [Google Pay](../Google-Pay/Google-Pay.md)