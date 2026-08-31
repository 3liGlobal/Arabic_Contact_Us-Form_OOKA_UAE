# Arabic_Contact_Us-Form_OOKA_UAE

> 3LI Global — AIR Global integration estate. Generated 2026-08-31 by the US-Infrastructure audit. Facts below are drawn from this repo's code; anything not directly evidenced is marked _unverified_.

## Connected Resource
- **Azure resource:** none — a single static `index.html` (no server, no build, no deploy workflow). _Actual hosting location is unverified; typically embedded in a web page or served as a static asset._
- **Deploy trigger:** none committed (no `.github/workflows`).
- **Talks to:**
  - **HubSpot Forms** — region `eu1`, portal `25636661`, form `502873f2-5ae3-4f2a-ae8d-25292033532b`, loaded via HubSpot's embed script `//js-eu1.hsforms.net/forms/embed/v2.js`. Submissions go straight to HubSpot.
  - **Bootstrap 4 CDN** (`cdn.jsdelivr.net`) for base styling.

## What It Does
Renders an Arabic-oriented **Contact Us** form for the OOKA UAE brand by embedding a HubSpot form and applying custom CSS — right-aligned fields/labels (`text-align: right`) for Arabic RTL, a purple gradient submit button, and restyled inputs, error messages, and required markers.

## Why It Exists
The customer-facing lead-capture form for OOKA in the UAE, wired directly to the **UAE HubSpot portal `25636661`** (the same portal used across AIR Global's UAE/OOKA HubSpot work). It is the presentation layer only — HubSpot owns the fields, validation, and storage; this repo just embeds and styles that form for the Arabic audience. No PreProd/Staging twin exists in the repo.

## How It Works
1. The page loads Bootstrap CSS and HubSpot's `embed/v2.js`.
2. `hbspt.forms.create({ region: "eu1", portalId: "25636661", formId: "502873f2-…", css: "…" })` injects the HubSpot form with the inline CSS overrides.
3. A `message` event listener captures an email value passed from a parent frame into `em` (an `onFormReady` prefill hook exists but is commented out) — i.e. it can be embedded inside another page that hands it the visitor's email. _Prefill is currently disabled in code._
4. On submit, HubSpot handles the POST and record creation; there is no custom backend here.
5. **Operator notes:** no secrets (the portal/form ids are public embed identifiers); changing fields is done in HubSpot, not in this file.

---
_Environment:_ unknown — static embed, not deployed from this repo (form itself is live in HubSpot)
_Runtime:_ static HTML/JS (HubSpot Forms embed + Bootstrap 4)
