---
name: anz-accounts-and-balances
description: List a consenting ANZ customer's accounts, read account detail and balances through the CDR data-holder API (ADR-gated).
api: openapi/anz-banking-accounts-api-openapi.yml
method: generated
generated: '2026-10-20'
operations: [listBankingAccounts, getBankingAccountDetail, listBankingBalancesBulk, listBankingBalancesSpecificAccounts, getBankingBalance]
---

# ANZ accounts and balances (CDR, gated)

Requires CDR accredited-data-recipient status, active consumer consent, an OAuth2/FAPI access token and mTLS.
Every call sends `x-v`; `x-fapi-interaction-id` is recommended for tracing.

## Steps
1. **List accounts** — `listBankingAccounts` — `GET /banking/accounts` (scope `bank:accounts.basic:read`; filters `product-category`, `open-status`, `is-owned`).
2. **Account detail** — `getBankingAccountDetail` — `GET /banking/accounts/{accountId}` (scope `bank:accounts.detail:read`).
3. **Balances** — all accounts with `listBankingBalancesBulk` (`GET /banking/accounts/balances`), a chosen set with
   `listBankingBalancesSpecificAccounts` (`POST /banking/accounts/balances`, body `data.accountIds[]` — a read, not a write),
   or one account with `getBankingBalance` (`GET /banking/accounts/{accountId}/balance`).

## Rules
- All operations are reads; the POST variant is a read with a request body and is safe to retry.
- `accountId` values are opaque, consent-scoped identifiers; never persist them beyond the consent.
