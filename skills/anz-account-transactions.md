---
name: anz-account-transactions
description: Pull and filter a consenting ANZ customer's account transactions and fetch one transaction's detail via the CDR API (ADR-gated).
api: openapi/anz-banking-account-transactions-api-openapi.yml
method: generated
generated: '2026-10-20'
operations: [listBankingAccounts, listBankingTransactions, getBankingTransactionDetail]
---

# ANZ account transactions (CDR, gated)

Scope `bank:transactions:read` (plus `bank:accounts.basic:read` to discover accounts). ADR + consent + FAPI + mTLS required.

## Steps
1. Find the account — `listBankingAccounts` (`openapi/anz-banking-accounts-api-openapi.yml`).
2. **List transactions** — `listBankingTransactions` — `GET /banking/accounts/{accountId}/transactions`,
   filter with `oldest-time`, `newest-time`, `min-amount`, `max-amount`, `text`; page with `page`/`page-size` and `links.next`.
3. **Transaction detail** — `getBankingTransactionDetail` — `GET /banking/accounts/{accountId}/transactions/{transactionId}`.

## Rules
- Read-only; safe to retry. Respect CDS paging links rather than constructing page URLs.
