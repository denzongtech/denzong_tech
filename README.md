# Denzong Tech — complete starter project

A responsive, mobile-first website for the Denzong Tech concept: local business growth services, AI-assisted marketing drafts, Denzong Stay enquiry requests, pricing, and lead capture through Netlify Forms.

## Project structure

```text
denzong-tech-complete/
├── netlify.toml
├── README.md
├── public/
│   └── index.html
└── netlify/
    └── functions/
        └── ai.mjs
```

## Before publishing

1. Open `public/index.html`.
2. Search for `91XXXXXXXXXX` and replace it with the real WhatsApp number, including country code 91 and no `+`, spaces, or dashes. If you are not ready to publish a number, leave the placeholder; WhatsApp buttons will warn the visitor instead of opening a broken chat.
3. Review the Starter, Growth and Premium inclusions/prices. These are proposed test packages, not independently verified market rates. Only sell work you can deliver reliably.
4. Review the privacy notice and contact details. Do not collect more customer information than needed.

## Deploy to Netlify from GitHub (recommended)

1. Upload the **contents** of this project to a GitHub repository. Keep `netlify.toml` at the repository root; keep the website at `public/index.html`; keep the backend at `netlify/functions/ai.mjs`.
2. In Netlify, open **Add new site / Import an existing project** and connect the repository (or update an existing Netlify site to use this repository).
3. Set the base directory to the repository root. The included `netlify.toml` sets publish directory to `public` and functions directory to `netlify/functions`; do not change these unless you also change the file structure.
4. Trigger a deploy. Wait until the deploy is marked published.
5. Open `https://YOUR-SITE.netlify.app/.netlify/functions/ai` in a browser. A JSON response saying the backend is deployed proves the function route is reachable. If it says `GEMINI_API_KEY is not configured`, the route works but AI is not enabled yet.

## Enable AI

1. Create an API key in Google AI Studio: https://aistudio.google.com/apikey
2. In Netlify, open the site's environment variables settings and add:
   - Key: `GEMINI_API_KEY`
   - Value: your private key copied from Google AI Studio
   - Scope: Functions/runtime (or all scopes if Netlify presents only that option)
   - Deploy context: all contexts
3. Optionally add `GEMINI_MODEL` with value `gemini-3.8-flash`. The function defaults to this model if the variable is absent.
4. Save the variables, then **trigger a fresh deploy**. Do not put the API key in `index.html`, GitHub, chat messages, or any public file.
5. Visit the health endpoint again. It should say `aiConfigured: true`; then test the AI workspace on the website.

API availability, quotas, rate limits, model names, and pricing can change. Check current Google AI Studio/API information if the model or quota is rejected. Free-tier data-use terms can differ from paid-tier terms; do not send private customer details or sensitive information to AI without checking the current provider terms and obtaining appropriate consent.

## Enquiries and forms

The site uses Netlify Forms for `business-leads` and `stay-enquiries`. After deploy, open the Netlify Forms area and confirm both forms are detected. Test a submission with your own details and verify it appears in the dashboard. Configure form notifications if available in your site's settings.

Denzong Stay is currently an **enquiry form**, not a live booking engine. It has no property inventory, live availability, booking confirmation, customer login, online payment, refunds, or owner portal. A hotel/homestay must manually confirm availability, price, taxes, cancellation terms, and the booking. Do not describe an enquiry as a confirmed booking.

## What is included / not included

Included: responsive frontend; package pages; AI-assisted content tools; server-side Gemini API call; health endpoint; basic per-instance burst protection; Netlify Forms-ready lead capture; WhatsApp handoff; explicit booking-enquiry language.

Not included: a relational database, authentication, role-based access, permanent hotel inventory, automated availability, payment gateway, invoice/tax engine, durable global rate limiting, analytics pipeline, CRM, or production security audit. These require additional services and careful configuration. The free/static site alone is not a complete production SaaS back office.

## Troubleshooting

- **404 at `/.netlify/functions/ai`:** check that `netlify/functions/ai.mjs` is committed in the repository, `netlify.toml` is at the repository root, the functions directory is `netlify/functions`, and a fresh Git-based deploy completed. A manual static drag-and-drop deployment does not build the function source.
- **`aiConfigured: false`:** set `GEMINI_API_KEY` in Netlify's runtime environment and redeploy.
- **401/403:** check the key, the Google AI project and API access.
- **429:** quota or request limit reached; check the API project's current quota.
- **Form not recorded:** verify Netlify detected the form after deploy, check the Forms dashboard, and test on the published URL (not just a local preview).
- **WhatsApp button warns:** replace `91XXXXXXXXXX` with your actual contact number.

## Safety and operations note

This is a starter implementation and should be tested before taking paying customers. If you are a government employee, obtain written clarification from the competent authority about whether and how paid private business activity is permitted before operating commercially. Seek appropriate professional advice for consumer terms, privacy, GST/tax, property partner agreements, and any future payment/commission model.
