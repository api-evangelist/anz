---
name: anz-regular-payments
description: Read a consenting ANZ customer's scheduled payments, instalment plans and direct debits via the CDR API (ADR-gated).
api: openapi/anz-banking-account-scheduled-payments-api-openapi.yml
method: generated
generated: '2026-10-20'
operations: [listScheduledPayments, listScheduledPaymentsBulk, listScheduledPaymentsSpecificAccounts, listInstalmentPlans, listInstalmentPlansBulk, listDirectDebits, listDirectDebitsBulk, listDirectDebitsSpecificAccounts]
---

# ANZ regular payments (CDR, gated)

Scope `bank:regular_payments:read`. ADR + consent + FAPI + mTLS required.
Direct-debit operations live in `openapi/anz-banking-account-direct-debits-api-openapi.yml`.

## Steps
1. **Scheduled payments** — per account `listScheduledPayments` (`GET /banking/accounts/{accountId}/payments/scheduled`),
   all accounts `listScheduledPaymentsBulk` (`GET /banking/payments/scheduled`), or a set `listScheduledPaymentsSpecificAccounts` (`POST`, body `data.accountIds[]`).
2. **Instalment plans** — `listInstalmentPlans` (`GET /banking/accounts/{accountId}/payments/plans`) or `listInstalmentPlansBulk` (`GET /banking/accounts/payments/plans`), filter `plan-status`.
3. **Direct debits** — `listDirectDebits`, `listDirectDebitsBulk`, or `listDirectDebitsSpecificAccounts` (`POST`, body `data.accountIds[]`).

## Rules
- All reads; POST variants carry a body but change nothing and are safe to retry.
