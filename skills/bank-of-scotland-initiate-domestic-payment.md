---
name: Initiate a Bank of Scotland domestic payment (PIS)
description: As an OBIE-registered PISP, create a domestic payment consent, get PSU authorisation, then submit the payment idempotently with a detached JWS signature. FAPI-secured (OAuth2/OIDC, mTLS, PSD2 SCA).
api: openapi/obie-payment-initiation-openapi.yaml
operations: [CreateDomesticPaymentConsents, GetDomesticPaymentConsentsConsentId, GetDomesticPaymentConsentsConsentIdFundsConfirmation, CreateDomesticPayments, GetDomesticPaymentsDomesticPaymentId]
---

# Initiate a Bank of Scotland domestic payment (PIS)

Base path: `/open-banking/v4.0/pisp`. Requires TPP onboarding, eIDAS/OBWAC-OBSEAL certificates, the `payments` scope, mutual-TLS, and detached JWS request signing.

## Steps

1. **Get a client token** — `TPPOAuth2Security` client_credentials flow, scope `payments`.
2. **Create the payment consent** — `CreateDomesticPaymentConsents` (`POST /domestic-payment-consents`). Send `x-idempotency-key` (max 40 chars) and `x-jws-signature`. Returns a `ConsentId`.
3. **PSU authorisation** — redirect the PSU through the `PSUOAuth2Security` authorization_code flow (OIDC + SCA) to authorise the consent.
4. **Confirm consent + funds** — `GetDomesticPaymentConsentsConsentId` until `Authorised`; optionally `GetDomesticPaymentConsentsConsentIdFundsConfirmation` (`GET /domestic-payment-consents/{ConsentId}/funds-confirmation`).
5. **Submit the payment** — `CreateDomesticPayments` (`POST /domestic-payments`) referencing the `ConsentId`, with a fresh `x-idempotency-key` and `x-jws-signature`. The `Initiation` object MUST match the consent exactly.
6. **Track status** — `GetDomesticPaymentsDomesticPaymentId` (`GET /domestic-payments/{DomesticPaymentId}`) to poll the payment status.

## Rules

- **Idempotency is mandatory** — reuse the same `x-idempotency-key` when retrying a submission so the payment is never duplicated (24h retention). A key reuse with a different body returns `409`.
- Sign every POST body with `x-jws-signature`; a missing/invalid signature yields `UK.OBIE.Signature.*`.
- `422` covers business rejections — `UK.OBIE.Rules.AfterCutOffDateTime`, `UK.OBIE.Rules.DuplicateReference`, insufficient funds.
- Send and log `x-fapi-interaction-id`; handle the `OBErrorResponse1` envelope (errors/bank-of-scotland-problem-types.yml).
