---
name: Look up Greater Bank banking products
description: >-
  Discover and inspect Greater Bank's publicly offered banking products
  (transaction/savings accounts, term deposits, home/personal loans, credit
  cards) via the public, unauthenticated CDR Product Reference Data API. No
  credentials required.
api: openapi/greater-bank-cds-banking-products-openapi.yml
base_url: https://public.cdr.greater.com.au/cds-au/v1
operations: [listBankingProducts, getBankingProductDetail]
auth: none
---

# Look up Greater Bank banking products

Greater Bank (brand `GB`, part of Newcastle Greater Mutual Group) publishes its
product catalogue as a public **CDR Product Reference Data (PRD)** API. It is
read-only and requires **no authentication** — only the mandatory `x-v` version
header.

## Rules an agent must follow

1. **Always send `x-v`.** Every request needs the `x-v` header (a positive
   integer). For the products list use `x-v: 4` (supported 4–5; the server
   replies with the highest supported version and echoes it in the response
   `x-v`). For product detail use `x-v: 7`. Omitting `x-v` returns `400`; an
   unsupported value returns `406 Unsupported Version`.
2. **Do not send credentials.** These endpoints are unauthenticated. OAuth is
   only for the separate accredited-data-recipient consumer-data tier, which is
   out of scope here.
3. **Errors** come back as `{ "errors": [ { "code", "title", "detail" } ] }`
   (CDS `ResponseErrorListV2`), not RFC 9457 problem+json. See
   `errors/greater-bank-problem-types.yml`.

## Step 1 — list products (`listBankingProducts`)

`GET /banking/products` with header `x-v: 4`.

Useful query params:
- `product-category` — filter to one category (e.g. `TRANS_AND_SAVINGS_ACCOUNTS`,
  `TERM_DEPOSITS`, `RESIDENTIAL_MORTGAGES`, `PERS_LOANS`, `CRED_AND_CHRG_CARDS`).
- `effective` — `CURRENT` (default), `FUTURE`, or `ALL`.
- `updated-since` — DateTimeString; only products changed after this time.
- `page`, `page-size` — standard pagination (defaults `page=1`, `page-size=25`).

Read `data.products[]` for each product's `productId`, `name`, `description`,
`productCategory`, and `brand`. Follow `meta.totalPages` / `links.next` to page
through the full set.

## Step 2 — get product detail (`getBankingProductDetail`)

For any `productId` from Step 1: `GET /banking/products/{productId}` with header
`x-v: 7`.

The detail payload extends the list item with `depositRates`, `lendingRates`,
`fees`, `features`, `constraints`, `eligibility`, and `bundles`, plus the
`additionalInformation` URIs (fees/eligibility/terms/overview) that link to the
bank's own web pages. A missing or invalid `productId` returns `404`.

## Notes

- CORS is open (`access-control-allow-origin: *`), so this works from browser
  tooling.
- Products are retired via `effectiveTo` rather than deletion; pass
  `effective=ALL` to also see future/expired offerings.
