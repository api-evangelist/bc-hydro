# BC Hydro (bc-hydro)

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

There is no `developer.bchydro.com`, `developers.bchydro.com`, `api.bchydro.com`, `docs.bchydro.com` or `data.bchydro.com` — all fail to resolve. There is no `/developers`, `/api` or `/data` path, no `/openapi.json` or `/swagger.json`, and no OpenAPI, Swagger, or Postman artifact anywhere across the 3,703 URLs in the site's own `sitemap.xml`. No open data portal is published.

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
