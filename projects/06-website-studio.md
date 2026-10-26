# Website Studio

**Oct 2026 · The team that builds customer websites**

## Problem

Customer websites were built by hand on a website builder. Intake answers sat in a spreadsheet, site status sat in Salesforce, and an automation only created a blank site. Nobody could see in one place which sites were stuck or what data was missing.

## What I built

- A **board** of every site by stage, with "stuck" flags per stage and the missing-data checks.
- A **site view** with the customer's intake answers next to their account.
- A **first draft of the site copy** from an LLM, which the builder edits and approves.

Version 1 is read-only towards Salesforce, the site builder and the support inbox. The only thing it writes is its own drafts table. The buttons for later versions (build the site, update status, ask the customer for missing data, publish) are visible but switched off.

## How it works

- A read-only Salesforce client and the Google sign-in module, both reused from my earlier apps.
- Drafts use structured JSON output from the Claude API, with a server-side fallback when the model refuses or the key is missing.
- The data source is a switch. Locally it runs on pretend data and an in-memory database, so the whole flow can be shown without touching real systems.

## Decisions worth explaining

- **Ship v1 read-only.** Each write needs its system owner's agreement. Showing the switched-off buttons made the roadmap concrete without the risk.
- **Treat guessed field names as guesses.** Field names I couldn't confirm are environment variables listed as unconfirmed in the README. A wrong one fails with an error that names the field.
- **Build a custom app over a no-code flow.** My access in the no-code tools was read-only, and the work needed a review screen anyway.

## Stack

Node, Express, Salesforce SOQL, Claude API (structured output), Postgres (pg-mem locally), Google OAuth, Node test runner.

## Talking points

- Using an LLM for a first draft that a person owns.
- Phasing integrations by risk: read, then draft, then write.
