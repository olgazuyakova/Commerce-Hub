## Transaction Interaction

The trasnaction request may contain the data regarding where the transaction is been acquired and what are the capabilities of the terminal.

| Variable | Type | Length | Description/Values |
| -------- | -- | ------------ | ------------------ |
| `origin` | *string* |  | The source of the transaction. [Available Values](#pos-entry-mode) |
| `posEntryMode` | *string* |  | An identifier used to indicate how the account number was entered on the transaction. [Available Values](#pos-entry-mode)|
| `posConditionCode` | *string* |  | An identifier used to indicate the transaction condition at the Point-of-Sale *(POS)*. [Available Values](#pos-condition-code)|
| `mobileInteraction` | *string* |  | Mobile method of interaction. [Available Values](#mobile-interaction)|
| `eciIndicator` | *string* |  | Electronic Commerce Indicator (ECI). [Available Values](#electronic-commerce-indicator)|

### Transaction Origin

The available values for `origin` are :

| Value | Description |
|-------|-------------|
| *ECOM* | Card Not Present email or internet. |
| *MOTO* | Mail order or telephone order. |
| *POS* | Card Present retail face to face. |

### POS Entry Mode

The available values for `posEntryMode` are :

| Value | Description |
|-------|-------------|
| *UNSPECIFIED* | Default |
| *MANUAL* | Key Entered |
| *BARCODE* | Barcode Scan |
| *OCR* | Optical Character Reader |
| *ICR_RELIABLE* | Integrated Circuit Read (CVV data Reliable) |
| *ICR_UNRELIABLE* | Integrated Circuit Read (CVV data unreliable) |
| *CONTACTLESS* | Contactless Integrated Circuit Read (Reliable) |
| *CONTACTLESS_MOBILE* | Contactless Mobile Commerce or Discover InApp |
| *CONTACTLESS_MAG_STRIPE* | Contactless Magnetic Stripe Read |
| *AMEX_WALLET* | Amex Digital Wallet |
| *MASTERCARD_REMOTE_CHIP* | Mastercard remote chip entry |
| *CREDENTIAL_ON_FILE* | Credential on File |
| *EMV_FALLBACK* | EMV fallback to manual entry |
| *EMV_FALLBACK_MAG* | EMV fallback to Magnetic Strip entry |
| *EMV_SWITCHED* | EMV Transaction switched from Contactless to Contact entry |
| *MAG_STRIPE* | Magnetic Stripe - Track Read |


### POS Condition Code

The available values for `posConditionCode` are :

| Value | Description |
|-------|-------------|
| *CARD_PRESENT* | Cardholder Present, Card Present. Designates a transaction where the cardholder was present at a merchant location. |
| *CARD_PRESENT_UNSPECIFIED* | Cardholder Present, Unspecified |
| *CARD_PRESENT_UNATTENDED* | Cardholder Present, Unattended Device. Designates a transaction where the cardholder was present at a merchant location and processed through an unattended device *(e.g. kiosk, gas pump)*. |
| *CARD_PRESENT_FRAUD* | Cardholder Present, Suspect Fraud. Designates a transaction where the cardholder was present at a merchant location, but the merchant suspects fraud. |
| *CARD_PRESENT_MAG_NOT_READ* | Cardholder Present, Magnetic Stripe Could Not Be Read. Designates a transaction where the cardholder was present at a merchant location but the MAG Stripe could not be read *(i.e. manual transaction)*. |
| *CARD_PRESENT_IDENTIFIED* | Cardholder Present, Identity Verified. Designates a transaction where the cardholder was present at a merchant location and their identity was verified. |
| *CARD_NOT_PRESENT_RECURRING* | Cardholder Not Present – Recurring. Designates a transaction that represents an arrangement between a cardholder and the merchant where transactions are going to occur on a periodic basis. |
| *CARD_NOT_PRESENT_INSTALLMENT* | Cardholder Not Present – Installment. Designates a group of transactions that originated from a single purchase where the merchant agrees to bill the cardholder in installments. |
| *CARD_NOT_PRESENT_DEFERRED* | Cardholder Not Present – Deferred. Designates a transaction that represents an order with a delayed payment for a specified amount of time. |
| *CARD_NOT_PRESENT_F2F* | Cardholder Present, Card Not Present, Face 2 Face. Designates a transaction where the cardholder was present at a merchant location but did not have a card to swipe. |
| *CARD_NOT_PRESENT_MOTO* | Cardholder Not Present, Mail Order/Telephone Order. Designates a transaction where the cardholder is not present at a merchant location and consummates the sale via the phone or through the mail. The transaction is not for recurring services or product and does not include sales that are processed via an installment plan. |
| *CARD_NOT_PRESENT_ECOM* | Cardholder Not Present, Ecommerce. Designates a transaction initiated from the merchant's website or email. |

### Mobile Interaction

The available values for `mobileInteraction` are :

| Value | Description |
|-------|-------------|
| *PHONE_NUMBER* | Invoice received by phone number |
| *QR_CODE* | Invoice paid by scanning QR Code |

### Electronic Commerce Indicator

The available values for `eciIndicator` are :

| Value | Description |
|-------|-------------|
| *SECURE_ECOM* | Secure Electronic Transaction. Designates a transaction between a cardholder and a merchant consummated via the Internet where the transaction was successfully authenticated and includes the management of a cardholder certificate. *(e.g. 3-D Secure Transactions)* |
| *NON_AUTH_ECOM* | Non-Authenticated Electronic Commerce Transaction. Designates a transaction consummated via the Internet at a 3-D Secure capable merchant that attempted to authenticate the cardholder using 3-D Secure. *(e.g. 3-D Secure includes Verified by Visa and MasterCard SecureCode)*. Attempts occur with Verified by Visa and MasterCard SecureCode transactions in the event of: A non-participating Issuer, a non-participating cardholder of a participating Issuer, or a participating Issuer, but the authentication server is not available. |
| *CHANNEL_ENCRYPTED* | Channel Encrypted Transaction. Designates a transaction between a cardholder and a merchant consummated via the Internet where the transaction includes the use of transaction encryption such as SSL, but authentication was not performed. The cardholder payment data was protected with a form of Internet security, such as SSL, but authentication was not performed. |
| *NON_SECURE_ECOM* | Non-Secure Electronic Commerce Transaction. Designates a transaction between a cardholder and a merchant consummated via the Internet where the transaction does not include the use of any transaction encryption such as SSL, no authentication performed, no management of a cardholder certificate. |