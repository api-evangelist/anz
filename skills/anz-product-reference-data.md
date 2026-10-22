---
name: anz-product-reference-data
description: Retrieve ANZ's publicly offered banking products and their full detail from the public, unauthenticated CDR Product Reference Data API.
api: openapi/anz-banking-products-api-openapi.yml
method: generated
generated: '2026-10-20'
operations: [listBankingProducts, getBankingProductDetail]
---

# List ANZ banking products (CDR Product Reference Data)

Public, **no authentication** — only the mandatory `x-v` version header (optionally `x-min-v`).
Hosts: ANZ `https://api.anz/cds-au/v1`, ANZ Plus `https://cdr.apix.anz/cds-au/v1`.

## Steps

1. **List products** — `listBankingProducts` — `GET /banking/products`.
   Optional query: `effective` (CURRENT|FUTURE|ALL), `updated-since`, `brand`, `product-category`, `page`, `page-size`.
   Read `data.products[]`; page with `links.next` / `meta.totalPages`.
2. **Get product detail** — `getBankingProductDetail` — `GET /banking/products/{productId}`
   using a `productId` from step 1. Detail adds fees, deposit/lending rates, eligibility, constraints and features.

## Rules
- Both calls are read-only GETs and safe to retry.
- An unsupported `x-v` returns a CDS error (`urn:au-cds:error:cds-all:Header/UnsupportedVersion`); retry with a supported version.
