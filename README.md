# Australia and New Zealand Banking Group (ANZ) (anz)

Australia and New Zealand Banking Group Limited (ANZ) is one of Australia's "Big Four" banks, a publicly listed company (ASX & NZX: ANZ) headquartered in Melbourne that provides retail, commercial, and institutional banking across Australia, New Zealand, and internationally. ANZ is a shareholder-owned Authorised Deposit-taking Institution (ADI) — not a mutual — regulated by APRA. As a designated data holder under Australia's Consumer Data Right (CDR / Open Banking), ANZ exposes a public, unauthenticated Product Reference Data (PRD) API conforming to the Data Standards Body (DSB) Consumer Data Standards, and operates a separate CDR brand endpoint for ANZ Plus.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/anz/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/anz/refs/heads/main/apis.yml)

## Tags

- Financial
- Banks
- Open Banking
- CDR
- Consumer Banking
- Australia
- Product Reference Data
- ADI

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-20

## APIs

### Australia and New Zealand Banking Group (ANZ) CDR Product Reference Data API

ANZ's public, unauthenticated Consumer Data Right Product Reference Data (PRD) API for the primary ANZ brand. It returns the bank's publicly offered banking products (accounts, cards, loans, overdrafts) as defined by the DSB Consumer Data Standards. Requires the CDS version header (x-v; version 4 and 5 confirmed live returning HTTP 200 with a data.products array).

- **Human URL:** [https://www.anz.com.au/support/legal/anz-apis/](https://www.anz.com.au/support/legal/anz-apis/)
- **Base URL:** `https://api.anz/cds-au/v1/banking/products`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Banking
- Public

#### Properties

- [Documentation](https://www.anz.com.au/support/legal/anz-apis/)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#cdr-banking-api_get-products)
- [OpenAPI](openapi/anz-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

### ANZ Plus CDR Product Reference Data API

The Consumer Data Right Product Reference Data API for ANZ's separate digital brand, ANZ Plus, served under its own CDR data-holder brand host. Public and unauthenticated, conforming to the same DSB Consumer Data Standards banking products contract (x-v version 4 and 5 confirmed live returning HTTP 200).

- **Human URL:** [https://www.anz.com.au/support/legal/anz-apis/](https://www.anz.com.au/support/legal/anz-apis/)
- **Base URL:** `https://cdr.apix.anz/cds-au/v1/banking/products`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- ANZ Plus
- Public

#### Properties

- [Documentation](https://www.anz.com.au/support/legal/anz-apis/)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#cdr-banking-api_get-products)
- [OpenAPI](openapi/anz-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

## Common Properties

- [Website](https://www.anz.com.au/)
- [Developer Portal](https://developer.online.anz.com/)
- [Documentation](https://www.anz.com.au/support/legal/anz-apis/)
- [GitHub Organization](https://github.com/ANZ-Bank)
- [LinkedIn](https://www.linkedin.com/company/anz)
- [Privacy Policy](https://www.anz.com.au/privacy/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
