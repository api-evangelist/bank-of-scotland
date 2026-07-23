# Bank of Scotland (bank-of-scotland)

Bank of Scotland is a UK high-street retail and commercial bank, founded in 1695 and headquartered in Edinburgh - one of the oldest banks in the United Kingdom and a wholly owned subsidiary brand of Lloyds Banking Group (alongside Lloyds Bank and Halifax). It is authorised by the Prudential Regulation Authority and regulated by the FCA and PRA, and as one of the mandated CMA9 account-providers it participates in the UK Open Banking regime under PSD2.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/bank-of-scotland/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/bank-of-scotland/refs/heads/main/apis.yml)

## Tags

- Financial Services
- Banking
- Open Banking
- PSD2
- OBIE
- CMA9
- United Kingdom
- Payments
- Account Information
- Open Data

## Timestamps

- **Created:** 2026-07-23
- **Modified:** 2026-07-23

## APIs

### Bank of Scotland Open Data API

PUBLIC, unauthenticated OBIE Open Data reference API exposing ATM locations, branch details, personal and business current account products, unsecured SME loans, and commercial credit card products. Confirmed live: all six resource endpoints return HTTP 200 with Open-Licence JSON.

- **Human URL:** [https://developer.lloydsbanking.com/open-data](https://developer.lloydsbanking.com/open-data)
- **Base URL:** `https://api.bankofscotland.co.uk/open-banking/v2.2`

#### Confirmed endpoints (HTTP 200)

- `GET /atms`
- `GET /branches`
- `GET /personal-current-accounts`
- `GET /business-current-accounts`
- `GET /unsecured-sme-loans`
- `GET /commercial-credit-cards`

#### Properties

- [OpenAPI](openapi/obie-opendata-swagger.json) — OBIE Open Data Standard (shared spec)
- [Documentation](https://developer.lloydsbanking.com/open-data)
- [API Reference](https://github.com/OpenBankingUK/opendata-api-spec-compiled)

### Bank of Scotland Account and Transaction Information API (AIS)

OBIE Read/Write Account and Transaction Information API - account details, balances, transactions, standing orders, direct debits, beneficiaries, statements, and products. FAPI-secured (OAuth2/OIDC, mTLS, PSD2 SCA); requires developer onboarding and eIDAS/OBIE certificates.

- **Human URL:** [https://developer.lloydsbanking.com/](https://developer.lloydsbanking.com/)

#### Properties

- [OpenAPI](openapi/obie-account-info-openapi.yaml) — shared OBIE Read/Write standard
- [Documentation](https://developer.lloydsbanking.com/)
- [API Reference](https://github.com/OpenBankingUK/read-write-api-specs)

### Bank of Scotland Payment Initiation API (PIS)

OBIE Read/Write Payment Initiation API - domestic, scheduled, standing order, international, and file payment consents and orders. FAPI-secured; requires developer onboarding and eIDAS/OBIE certificates.

- **Human URL:** [https://developer.lloydsbanking.com/](https://developer.lloydsbanking.com/)

#### Properties

- [OpenAPI](openapi/obie-payment-initiation-openapi.yaml) — shared OBIE Read/Write standard
- [Documentation](https://developer.lloydsbanking.com/)
- [API Reference](https://github.com/OpenBankingUK/read-write-api-specs)

### Bank of Scotland Confirmation of Funds API (CBPII)

OBIE Read/Write Confirmation of Funds API - card-based payment instrument issuers confirm whether funds are available on an account. FAPI-secured; requires developer onboarding and eIDAS/OBIE certificates.

- **Human URL:** [https://developer.lloydsbanking.com/](https://developer.lloydsbanking.com/)

#### Properties

- [OpenAPI](openapi/obie-confirmation-funds-openapi.yaml) — shared OBIE Read/Write standard
- [Documentation](https://developer.lloydsbanking.com/)
- [API Reference](https://github.com/OpenBankingUK/read-write-api-specs)

## Common Properties

- [Website](https://www.bankofscotland.co.uk/)
- [Developer Portal](https://developer.lloydsbanking.com/)
- [Documentation](https://www.bankofscotland.co.uk/aboutonline/security-and-privacy/open-banking-apis.html)
- [LinkedIn](https://www.linkedin.com/company/bank-of-scotland)
- [Terms of Service](https://www.bankofscotland.co.uk/legal.html)
- [Privacy Policy](https://www.bankofscotland.co.uk/legal/privacy.html)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
