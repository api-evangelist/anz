---
name: anz-payees
description: List a consenting ANZ customer's saved payees and read one payee's detail via the CDR API (ADR-gated).
api: openapi/anz-banking-payees-api-openapi.yml
method: generated
generated: '2026-10-20'
operations: [listBankingPayees, getBankingPayeeDetail]
---

# ANZ payees (CDR, gated)

Scope `bank:payees:read`. ADR + consent + FAPI + mTLS required.

## Steps
1. **List payees** — `listBankingPayees` — `GET /banking/payees` (optional `type` filter, paging).
2. **Payee detail** — `getBankingPayeeDetail` — `GET /banking/payees/{payeeId}`.

## Rules
- Read-only; safe to retry.
