# Aldermore Bank (aldermore)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Aldermore Bank plc is a UK specialist bank founded in 2009 and headquartered in Reading, offering savings accounts and specialist lending across residential and buy-to-let mortgages, commercial and property finance, asset finance, invoice finance, and motor finance (through sister company MotoNovo Finance). Aldermore Group is wholly owned by South Africa's FirstRand Group (acquired 2018; a sale/exit process began in 2026). Aldermore Bank plc is authorised by the PRA and regulated by the FCA and PRA (Financial Services Register number 204503). It is a branchless, digitally-delivered specialist lender rather than a full-service current-account bank, and it is NOT one of the CMA9. Because it does not provide current accounts, its UK Open Banking (OBIE / PSD2) payment-account footprint is minimal.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/aldermore/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/aldermore/refs/heads/main/apis.yml)

## Public API posture

At bootstrap, no public Aldermore developer portal, Open Data endpoint, or bank-proprietary API surface could be confirmed:

- No `developer.`, `api.`, `openbanking.`, or `apis.aldermore.co.uk` subdomain resolves.
- The bank's site (legal, contact, investors pages) makes no mention of a developer program, API, Open Banking, or Open Data.
- Aldermore does not appear in community/OBIE lists of UK Open Data publishers (which are dominated by the CMA9).
- A `https://www.aldermore.co.uk/.well-known/open-banking/config.json` probe returned HTTP 404.

The OBIE API families below are therefore represented as the **shared UK Open Banking standard, unverified for this bank** — the harvested specs are the Open Banking Implementation Entity reference contracts, not Aldermore-published contracts.

## Tags

- Financial Services
- Banking
- Savings
- Specialist Lending
- Open Banking
- PSD2
- OBIE
- United Kingdom
- Payments
- Account Information

## Timestamps

- **Created:** 2026-07-23
- **Modified:** 2026-07-23

## APIs

### Aldermore Open Data API (OBIE Standard)

The UK Open Banking Open Data API standard (public, unauthenticated reference data — products, ATMs, branches). No Aldermore Open Data endpoint confirmed; as a branchless lender its Open Data scope is minimal.

- **Human URL:** [https://openbankinguk.github.io/opendata-api-docs-pub/v2.4.0/](https://openbankinguk.github.io/opendata-api-docs-pub/v2.4.0/)

#### Properties

- [OpenAPI](openapi/aldermore-obie-open-data-openapi.json) — OBIE shared Open Data standard (Swagger 2.0)
- [Documentation](https://openbankinguk.github.io/opendata-api-docs-pub/v2.4.0/)
- [API Reference](https://github.com/OpenBankingUK/opendata-api-spec-compiled)

### Aldermore Account & Transaction Information API (OBIE Read/Write Standard)

The UK Open Banking Read/Write AIS standard — FAPI-secured (OAuth2/OIDC, mutual-TLS, PSD2 SCA). Represented as the shared OBIE standard; no Aldermore AIS endpoint or onboarding confirmed.

- **Human URL:** [https://openbankinguk.github.io/read-write-api-site3/](https://openbankinguk.github.io/read-write-api-site3/)

#### Properties

- [OpenAPI](openapi/aldermore-obie-account-info-openapi.yaml) — OBIE shared Read/Write standard (OpenAPI 3.0)
- [Documentation](https://openbankinguk.github.io/read-write-api-site3/)
- [API Reference](https://github.com/OpenBankingUK/read-write-api-specs)

### Aldermore Payment Initiation API (OBIE Read/Write Standard)

The UK Open Banking Read/Write PIS standard — FAPI-secured (OAuth2/OIDC, mutual-TLS, PSD2 SCA). Represented as the shared OBIE standard; no Aldermore PIS endpoint or onboarding confirmed.

- **Human URL:** [https://openbankinguk.github.io/read-write-api-site3/](https://openbankinguk.github.io/read-write-api-site3/)

#### Properties

- [OpenAPI](openapi/aldermore-obie-payment-initiation-openapi.yaml) — OBIE shared Read/Write standard (OpenAPI 3.0)
- [Documentation](https://openbankinguk.github.io/read-write-api-site3/)
- [API Reference](https://github.com/OpenBankingUK/read-write-api-specs)

### Aldermore Confirmation of Funds API (OBIE Read/Write Standard)

The UK Open Banking Read/Write CBPII standard — FAPI-secured (OAuth2/OIDC, mutual-TLS, PSD2 SCA). Represented as the shared OBIE standard; no Aldermore CBPII endpoint or onboarding confirmed.

- **Human URL:** [https://openbankinguk.github.io/read-write-api-site3/](https://openbankinguk.github.io/read-write-api-site3/)

#### Properties

- [OpenAPI](openapi/aldermore-obie-confirmation-of-funds-openapi.yaml) — OBIE shared Read/Write standard (OpenAPI 3.0)
- [Documentation](https://openbankinguk.github.io/read-write-api-site3/)
- [API Reference](https://github.com/OpenBankingUK/read-write-api-specs)

## Common Properties

- [Website](https://www.aldermore.co.uk/)
- [GitHub Organization](https://github.com/aldermore)
- [LinkedIn](https://www.linkedin.com/company/aldermorebank)
- [Support](https://www.aldermore.co.uk/contact-us/)
- [Terms of Service](https://www.aldermore.co.uk/legal/terms-and-conditions/)
- [Privacy Policy](https://www.aldermore.co.uk/legal/privacy-policy/)
- [Legal](https://www.aldermore.co.uk/legal/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
