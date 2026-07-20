---
name: List ANZ banking products (CDR Product Reference Data)
description: Retrieve ANZ's publicly offered banking products and their full detail from the public, unauthenticated CDR Product Reference Data API.
api: openapi/anz-cds-banking-products-openapi.yml
method: generated
generated: '2026-07-20'
operations: [listBankingProducts, getBankingProductDetail]
---

# List ANZ banking products (CDR Product Reference Data)

ANZ's Product Reference Data (PRD) API is **public and requires no authentication** —
only the mandatory `x-v` version header. It works on two brand hosts:

- ANZ: `https://api.anz/cds-au/v1`
- ANZ Plus: `https://cdr.apix.anz/cds-au/v1`

## Steps

1. **List products** — `listBankingProducts`
   `GET /banking/products` with header `x-v: 5`.
   Optional query params: `effective` (`CURRENT`|`FUTURE`|`ALL`, default `CURRENT`),
   `product-category`, `brand`, `page`, `page-size` (default 25).
   Read `data.products[]`; page through using `meta.totalPages` / `links.next`.

2. **Get one product's detail** — `getBankingProductDetail`
   `GET /banking/products/{productId}` with header `x-v: 7`, where `productId`
   comes from a `data.products[].productId` in step 1.
   The detail response adds `bundles`, `features`, `constraints`, `eligibility`,
   `fees`, `depositRates`, and `lendingRates`.

## Rules

- **Version header is mandatory.** Send `x-v` (the confirmed live values are 5 for the
  list and 7 for detail). A missing/invalid `x-v` returns `400`; an unsupported version
  returns `406`.
- **Errors** use the CDR error list format (`{ "errors": [ { code, title, detail } ] }`,
  `urn:au-cds:error:*` codes) — not RFC 9457. See `errors/anz-problem-types.yml`.
- **Pagination** is page-number based (`page`/`page-size`, `meta.totalRecords`/`totalPages`).
  See `conventions/anz-conventions.yml`.
- **No idempotency key** is needed — these are read-only GET calls.
- Check `GET /discovery/status` and `/discovery/outages` (also public) before treating a
  non-200 as a client error. See `lifecycle/anz-lifecycle.yml`.
- Anything beyond product reference data (accounts, balances, transactions) requires CDR
  accreditation (ADR) with OAuth2/FAPI + mTLS and consumer consent — see
  `authentication/anz-authentication.yml`.
