# Merchant Details

## Overview

Used to pass merchant data during the transaction and contains data like the merchant ID (MID), store ID, terminal ID (TID), MCC etc.

#### Component: merchantDetails

| Variable | Type | Length | Description/Values |
| -------- | -- |------------| ------------------ |
| `tokenType` | *string* |  | Specific Token Type is assigned to each merchant; example; TRANSARMOR. |
| `storeId` | *string* |  | An optional outlet ID for clients that support multiple stores in the same app. |
| `siteId` | *string* |  | The location ID or number used to identify the unique site and merchant. |
| `merchantId` | *string* |  | A unique ID used to identify the Merchant. The merchant must use the value assigned by the acquirer or the gateway when submitting a transaction. Utilizedfor clients that support [dynamic descriptor](?path=docs/Resources/Guides/Dynamic-Descriptor.md), or support multiple stores in the same app. |
| `terminalId` | *string* |  | Identifies the specific device or point of entry where the transaction originated. For example, pump number, lane number, terminal number, etc. |
| `alternateMerchantId` | *string* |  | An Alternate ID assigned to a merchant based on a Value Added Service (Prepaid Cards, TeleCheck, etc.). For additional information regarding the Alternate Merchant ID, please contact your account representative. |
| `promotionCode` | *string* |  | This field contains the Promotion Code. |
| `mcc` | *string* |  | [Merchant Category Code](?path=docs/Resources/Master-Data/Merchant-Category-Code.md). |

---

## See Also

- [API Explorer](../api/?type=post&path=/payments/v1/charges)
- [Dynamic Descriptor](?path=docs/Resources/Guides/Dynamic-Descriptor.md)
- [Merchant Category Codes](?path=docs/Resources/Master-Data/Merchant-Category-Code.md)
- [Payment Facilitators](?path=docs/Resources/Guides/Industry-Verticals/Payment-Faciliator.md)

---
