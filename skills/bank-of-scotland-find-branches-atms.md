---
name: Find Bank of Scotland branches and ATMs
description: Look up Bank of Scotland branch and ATM locations and product reference data using the public, unauthenticated OBIE Open Data API. No credentials or consent required.
api: openapi/obie-opendata-swagger.json
operations: [GET /branches, GET /atms, GET /personal-current-accounts]
---

# Find Bank of Scotland branches and ATMs

This flow uses the **public Open Data API** — it is unauthenticated and safe to call directly. Base URL: `https://api.bankofscotland.co.uk/open-banking/v2.2`.

## Steps

1. **List branches** — `GET /branches`. Returns all branch objects (name, address, geolocation, services, opening hours). Supports `If-Modified-Since` / `If-None-Match` conditional headers to avoid re-fetching unchanged data.
2. **List ATMs** — `GET /atms`. Returns ATM locations, capabilities and accessibility features.
3. **List products** — `GET /personal-current-accounts`, `GET /business-current-accounts`, `GET /unsecured-sme-loans`, `GET /commercial-credit-cards` for product reference data.

## Rules

- Responses are Open-Licence JSON; the `produces` media type is `application/prs.openbanking.opendata.v1.3+json`.
- Cache using the ETag / Last-Modified response headers; poll with conditional requests.
- Handle `408`, `429`, `500`, `503` with backoff; `429` indicates rate limiting.
- Do NOT send credentials — this API rejects nothing but expects none.
