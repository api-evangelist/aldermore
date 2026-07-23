---
name: Initiate a domestic payment (OBIE PIS)
description: Create a domestic-payment consent, obtain PSU authorisation, then execute and confirm a domestic payment under the UK Open Banking Read/Write standard, using idempotency for at-most-once execution.
api: openapi/aldermore-obie-payment-initiation-openapi.yaml
operations:
  - CreateDomesticPaymentConsents
  - GetDomesticPaymentConsentsConsentId
  - CreateDomesticPayments
  - GetDomesticPaymentsDomesticPaymentId
---

# Initiate a domestic payment (OBIE PIS)

This skill covers the UK Open Banking (OBIE) Read/Write **Payment Initiation Services**
happy path. It reflects the shared OBIE standard carried in this repo; a live deployment
requires PISP onboarding through the ASPSP/OBIE directory.

## Prerequisites
- You are an FCA/OBIE-registered TPP (PISP) with transport + signing certificates and MTLS.
- A client-credentials access token (`TPPOAuth2Security`, scope `payments`).

## Steps
1. **Create the payment consent** — `CreateDomesticPaymentConsents` with the
   `Initiation` block (`InstructedAmount`, `CreditorAccount`, `RemittanceInformation`).
   Sign the request per OBIE and capture the `ConsentId`.
2. **PSU authorisation** — redirect the PSU through the `authorizationCode` flow
   (`PSUOAuth2Security`) to complete SCA and authorise the specific payment consent.
3. **Confirm consent** — `GetDomesticPaymentConsentsConsentId`; proceed only when
   `Status` is `Authorised`.
4. **Execute the payment** — `CreateDomesticPayments` with the **same** `Initiation`
   block plus the `ConsentId`. Set the **`x-idempotency-key`** header (≤40 chars) so a
   safe retry never creates a duplicate payment.
5. **Confirm execution** — `GetDomesticPaymentsDomesticPaymentId` to read the final
   `Status` (`AcceptedSettlementInProcess` / `AcceptedSettlementCompleted`).

## Conventions & errors
- **Idempotency is mandatory on execution** — replay the identical body with the same
  `x-idempotency-key` to retry safely (see `conventions/aldermore-conventions.yml`).
- Verify the executed `Initiation` matches the consented `Initiation` exactly, or the
  ASPSP rejects with an `OBErrorResponse` (`422`).
- Echo `x-fapi-interaction-id`; handle `409` (idempotency/consent conflict) and `429`.
  See `errors/aldermore-problem-types.yml`.
