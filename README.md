# Greater Bank (greater-bank)

Greater Bank is a customer-owned Australian retail bank headquartered in Newcastle, New South Wales. In March 2023 it merged with Newcastle Permanent to form Newcastle Greater Mutual Group (NGM Group), one of Australia's largest customer-owned mutual banking organisations, while continuing to trade under the Greater Bank brand. As an Authorised Deposit-taking Institution (ADI) it is a designated data holder under Australia's Consumer Data Right (CDR / Open Banking).

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/greater-bank/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/greater-bank/refs/heads/main/apis.yml)

## Tags

- Financial
- Banks
- Open Banking
- CDR
- Consumer Banking
- Australia
- Mutual
- Product Reference Data

## Timestamps

- **Created:** 2026-07-20
- **Modified:** 2026-07-20

## APIs

### Greater Bank CDR Product Reference Data API

Public, unauthenticated Consumer Data Right Product Reference Data (PRD) API for Greater Bank, served under the standard CDS base path `cds-au/v1/banking/products`. Confirmed live returning HTTP 200 with an `x-v` response version of 4 (supported versions 4-5) and a `data.products` array covering transaction accounts, savings accounts, term deposits, home loans, personal loans, and credit cards under brand "GB" / brandName "Greater Bank". Exposes `GET /banking/products` (list, with filters and pagination) and `GET /banking/products/{productId}` (detail), each requiring the `x-v` version header. Conforms to the DSB Consumer Data Standards CDR Banking API contract.

- **Human URL:** [https://www.greater.com.au/openbanking](https://www.greater.com.au/openbanking)
- **Base URL:** `https://public.cdr.greater.com.au/cds-au/v1/banking/products`

#### Tags

- CDR
- Open Banking
- Product Reference Data
- Banking Products
- Australia

#### Properties

- [Documentation](https://www.greater.com.au/openbanking)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/#get-products)
- [OpenAPI](openapi/greater-bank-cds-banking-products-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)

> The harvested OpenAPI is the shared Data Standards Body (DSB) Consumer Data Standards "CDR Banking API" contract (the specification every Australian data holder implements for these endpoints), not a Greater Bank proprietary specification.

## Common Properties

- [Website](https://www.greater.com.au/)
- [Documentation](https://www.greater.com.au/openbanking)
- [API Reference](https://consumerdatastandardsaustralia.github.io/standards/)
- [Terms of Service](https://www.greater.com.au/termsandconditions)
- [LinkedIn](https://www.linkedin.com/company/greater-bank)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
