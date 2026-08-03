# Bank of Scotland (bank-of-scotland)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
