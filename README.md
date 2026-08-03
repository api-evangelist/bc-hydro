# BC Hydro (bc-hydro)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

British Columbia Hydro and Power Authority (BC Hydro) is a provincial Crown corporation whose sole shareholder is the Province of British Columbia, and which states that it generates and delivers electricity to "95% of the population of B.C." and serves "over five million people." It is the vertically integrated end of the value chain in a market with no retail competition: BC Hydro owns the generation fleet (predominantly large hydroelectric), owns and operates the provincial transmission and distribution system, and is the monopoly retailer that bills the customer — all under rate regulation by the B.C. Utilities Commission (BCUC), not under any consumer data right.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/bc-hydro/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/bc-hydro/refs/heads/main/apis.yml)

## Tags

- Energy
- Canada
- Utilities
- Electricity
- Crown Corporation
- Hydroelectric
- Renewables
- Grid
- Transmission
- Distribution
- Smart Metering
- Green Button
- Energy Data
- EV Charging

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

None. BC Hydro documents no public API.

There is no `developer.bchydro.com`, `developers.bchydro.com`, `docs.bchydro.com` or `data.bchydro.com` — none resolve. There is no `/developers`, `/api` or `/data` path, no `/openapi.json` or `/swagger.json`, and no OpenAPI, Swagger, or Postman artifact anywhere across the 3,703 URLs in the site's own `sitemap.xml`. No open data portal is published.

`api.bchydro.com` does resolve — to a BC Hydro-owned IP that completes a TLS 1.3 handshake with a valid Entrust OV certificate issued to "British Columbia Hydro and Power Authority" — but it refuses TLS 1.2 and returns nothing to any anonymous HTTP request on any path. A BC Hydro API host exists; nothing about it is public or documented, so it is not listed as an API.

## Energy data posture

- **Mandate regime:** `green-button-voluntary`. No consumer energy data mandate binds BC Hydro. Ontario Regulation 633/21 compels Ontario distributors to implement Green Button Download My Data and Connect My Data; it has no force in British Columbia, and Canada has no federal energy equivalent.
- **Mandate status:** `voluntary-adopted`. BC Hydro's own billing page states a customer can "Download a CSV or Green Button XML file with your metered electricity use," available through the previous day, with up to three years of history. No Green Button Alliance certification, ESPI version, or conformance claim was found, and the file could not be inspected because it is emitted only inside an authenticated session.
- **Data standard:** Green Button / ESPI, Download My Data file export only. No Connect My Data. No CDR Consumer Data Standards, OCPP, OCPI, OpenADR, IEEE 2030.5, or IEC CIM reference anywhere on the site.
- **Consumer data API:** No. A third party cannot obtain a customer's usage or billing data through any documented API. Only the account holder can, by signing in and downloading a file.
- **Market data open:** No. Wholesale transmission information goes to an OATI-hosted OASIS node open to "registered users" only, and the BCUC Order G-127-06 transaction-data postings are documents. The only deliberate open-data artifact is one 2013 mapping layer in the provincial BC Data Catalogue under the org `bc-hydro-and-power-authority`.
- **Access gate:** `customer-account-required`. There is nothing for a developer to sign up for — be a BC Hydro customer, register for MyHydro, sign in, download your own file.
- **Auth model:** Customer-portal session SSO. `https://www.bchydro.com/login` redirects to a ForgeRock/OpenAM-style endpoint at `https://app.bchydro.com/sso/UI/Login?goto=...&realm=bch-ps`. No OAuth 2.0 authorization or token endpoint for third parties, no client registration, no mTLS, no accreditation path. `/.well-known/openid-configuration` is rejected by the site WAF rather than served.
- **Home market:** Canada — British Columbia.

Full probe log, HTTP statuses, and evidence are recorded in [review.yml](review.yml).

## Artifacts

Every artifact below records what was probed and what was found — the misses are the finding.

- [authentication/bc-hydro-authentication.yml](authentication/bc-hydro-authentication.yml) — MyHydro customer-portal SSO (ForgeRock/OpenAM, realm `bch-ps`); no third-party auth, no OAuth, no discovery document.
- [conventions/bc-hydro-conventions.yml](conventions/bc-hydro-conventions.yml) — the semantics of the two real surfaces: the authenticated file export and the undocumented outage JSON feed (soft 404s, WAF behaviour, epoch-ms timestamps, no pagination, no idempotency).
- [conformance/bc-hydro-conformance.yml](conformance/bc-hydro-conformance.yml) — Green Button DMD yes / CMD no, no OAuth, no OIDC, no OpenAPI, plus TLS/DNSSEC/DMARC and the NERC CIP-013-2 supplier programme.
- [lifecycle/bc-hydro-lifecycle.yml](lifecycle/bc-hydro-lifecycle.yml) — no API versioning, deprecation policy, SLA, changelog or status page; the regulated tariff lifecycle instead.
- [packages/bc-hydro-packages.yml](packages/bc-hydro-packages.yml) — no first-party SDK in any registry, no GitHub org; one unofficial community Python package.
- [well-known/bc-hydro-well-known.yml](well-known/bc-hydro-well-known.yml) — the full `/.well-known/` probe index (all soft 404s) plus the `api.bchydro.com` TLS finding.
- [security/bc-hydro-domain-security.yml](security/bc-hydro-domain-security.yml) — TLS 1.3, HSTS, DNSSEC signed, SPF, DMARC `p=reject`, no CAA.
- [json-schema/bc-hydro-outages-map.json](json-schema/bc-hydro-outages-map.json) + [examples/](examples/bc-hydro-outages-map-example.json) — a schema **derived by API Evangelist** from a live fetch of the undocumented outage-map feed. Not a BC Hydro contract.
- [llms/bc-hydro-llms.txt](llms/bc-hydro-llms.txt) — generated agent briefing on what exists and what does not.

No `openapi/`, `overlays/`, `errors/`, `scopes/`, `data-model/`, `skills/`, `mcp/`, `arazzo/`, `asyncapi/`, `sandbox/`, `cli/`, `components/` or `changelog/` artifacts were created: there is no specification to ground them in and BC Hydro publishes none of those surfaces. Nothing was invented to fill a directory.

## Common Properties

- [Website](https://www.bchydro.com/)
- [About](https://www.bchydro.com/about.html)
- [Documentation — bill, billing history and Green Button XML / CSV downloads](https://app.bchydro.com/accounts-billing/bill-payment/view-bill.html)
- [Documentation — access load data](https://app.bchydro.com/accounts-billing/rates-energy-use/access-load-data.html)
- [Authentication — MyHydro login](https://www.bchydro.com/login)
- [Privacy Policy](https://www.bchydro.com/siteinfo/privacy.html)
- [Blog / Press Centre](https://www.bchydro.com/news/press_centre.html)
- [LinkedIn](https://www.linkedin.com/company/bc-hydro)
- [Regulator — B.C. Utilities Commission](https://www.bcuc.com/)
- [Standard — Green Button Alliance](https://www.greenbuttonalliance.org/)

## Maintainers

- Kin Lane — kin@apievangelist.com
