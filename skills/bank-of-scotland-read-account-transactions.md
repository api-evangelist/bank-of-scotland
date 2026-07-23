---
name: Read Bank of Scotland account transactions (AIS)
description: As an OBIE-registered AISP, establish an account-access consent, obtain PSU authorisation, then read accounts, balances and transactions. FAPI-secured (OAuth2/OIDC, mTLS, PSD2 SCA).
api: openapi/obie-account-info-openapi.yaml
operations: [CreateAccountAccessConsents, GetAccountAccessConsentsConsentId, GetAccounts, GetAccountsAccountId, GetAccountsAccountIdBalances, GetAccountsAccountIdTransactions]
---

# Read Bank of Scotland account transactions (AIS)

Base path: `/open-banking/v4.0/aisp`. Requires TPP onboarding via the Lloyds Banking Group developer platform, eIDAS/OBWAC-OBSEAL certificates, and the `accounts` scope. All requests use mutual-TLS.

## Steps

1. **Get a client token** — `TPPOAuth2Security` client_credentials flow, scope `accounts`.
2. **Create the consent** — `CreateAccountAccessConsents` (`POST /account-access-consents`) with the requested `Permissions[]`. Returns a `ConsentId`.
3. **PSU authorisation** — redirect the PSU through the `PSUOAuth2Security` authorization_code flow (OIDC + SCA) for that `ConsentId`; receive a PSU access token.
4. **Confirm consent status** — `GetAccountAccessConsentsConsentId` (`GET /account-access-consents/{ConsentId}`) until status is `Authorised`.
5. **List accounts** — `GetAccounts` (`GET /accounts`).
6. **Read balances** — `GetAccountsAccountIdBalances` (`GET /accounts/{AccountId}/balances`).
7. **Read transactions** — `GetAccountsAccountIdTransactions` (`GET /accounts/{AccountId}/transactions`), paging via the `Links.Next` cursor and filtering with `fromBookingDateTime` / `toBookingDateTime`.

## Rules

- Send `x-fapi-interaction-id` (UUID) on every call and log the echoed value for tracing.
- Handle the OBIE `OBErrorResponse1` envelope; `403` usually means the resource is outside the granted consent (see errors/bank-of-scotland-problem-types.yml).
- `401` → refresh/re-authenticate; `UK.OBIE.Reauthenticate` requires a fresh SCA.
- Respect `RateLimit` / `RateLimit-Policy` headers; back off on `429`.
