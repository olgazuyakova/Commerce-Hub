---
tags: [carat, commerce-hub, card-not-present, card-present, hash, primary-transactions, secondary-transactions]
---

# Transaction Types

## Overview

The Commerce Hub API allows a merchant to create, inquire, and finalize payment transactions. Our API has two transaction types; primary and secondary.

### Primary Transactions

Primary transactions include; [charge](../Transactions/Charges.md), [verification](../Transactions/Verification.md) and [information lookup](../Transactions/Information-Lookup.md) requests that are submitted without reference to a prior transaction.

### Secondary Transactions

Secondary Transactions include; [refund](../Transactions/Refund.md), [void](../Transactions/Cancel.md), [capture](../Transactions/Capture.md), and [inquiry](../Transactions/Inquiry.md) using the `transactionId` or `orderId` from a prior request.

- 'transactionID`: Transaction identifier returned in the *transactionProcessingDetails* of the *gatewayResponse*.

<!-- theme: example -->
>**Example Endpoint:** `/payments/v1/charges/{transactionId}/capture`

- `orderID`: Order identifier returned in the *gatewayResponse*.

<!-- theme: example -->
>**Example Endpoint:** `/payments/v1/charges/orders/{orderId}/capture`

---

## See Also

- [API Explorer](url)