---
name: Retrieve account and transaction information (OBIE AIS)
description: Establish an account-access consent, complete PSU authorisation, then read accounts, balances and transactions under the UK Open Banking Read/Write standard.
api: openapi/aldermore-obie-account-info-openapi.yaml
operations:
  - CreateAccountAccessConsents
  - GetAccountAccessConsentsConsentId
  - GetAccounts
  - GetAccountsAccountIdBalances
  - GetAccountsAccountIdTransactions
---

# Retrieve account and transaction information (OBIE AIS)

This skill covers the UK Open Banking (OBIE) Read/Write **Account Information Services**
happy path. It reflects the shared OBIE standard carried in this repo — Aldermore was
not confirmed to publish its own Open Banking developer portal, so a live deployment
requires TPP onboarding through the relevant ASPSP/OBIE directory.

## Prerequisites
- You are an FCA/OBIE-registered TPP (AISP) with an eIDAS/OBIE transport + signing certificate.
- Mutual-TLS (MTLS) is established with the ASPSP token and resource endpoints.
- A client-credentials access token (`TPPOAuth2Security`, scope `accounts`) for consent creation.

## Steps
1. **Create the consent** — `CreateAccountAccessConsents` with the `Permissions` you need
   (e.g. `ReadAccountsBasic`, `ReadBalances`, `ReadTransactionsCredits`). Send
   `x-fapi-interaction-id` for traceability. Capture the returned `ConsentId`.
2. **PSU authorisation** — redirect the PSU through the OAuth `authorizationCode` flow
   (`PSUOAuth2Security`) so they complete PSD2 Strong Customer Authentication and
   authorise the consent. You receive a PSU access token bound to the `ConsentId`.
3. **Confirm consent status** — `GetAccountAccessConsentsConsentId` and verify
   `Status` is `Authorised` before reading data.
4. **List accounts** — `GetAccounts` with the PSU token to enumerate authorised accounts
   and their `AccountId`s.
5. **Read balances** — `GetAccountsAccountIdBalances` per `AccountId`.
6. **Read transactions** — `GetAccountsAccountIdTransactions`; page with the `Links`
   (`Self`/`Next`) and `Meta` objects in the response envelope.

## Conventions & errors
- Echo `x-fapi-interaction-id` on every call; it correlates to the error `Id`.
- Errors return the `OBErrorResponse` envelope (`Code`, `Id`, `Message`, `Errors[]` with
  OBIE `ErrorCode`). Handle `403` (missing permission/consent) and `429` (rate limit)
  explicitly. See `errors/aldermore-problem-types.yml` and `conventions/aldermore-conventions.yml`.
