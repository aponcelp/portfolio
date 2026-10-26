# CX Capacity Planner

**Jun – Oct 2026 · Onboarding and Customer Success leadership**

## Problem

Leadership planned staffing from spreadsheets that someone rebuilt by hand each week. Nobody could say how many onboardings each specialist carried right now, or how load would change as signups grew.

## What I built

A planning app with tabs for Onboarding, Customer Success and, later, revenue forecasting. It started as a static page that read JSON snapshots. Over the summer it became a small server that reads Salesforce live.

- Open onboardings per specialist, counted only on customers with an active subscription.
- Customer Success book sizes and load per CSM.
- A flag for accounts stuck in a stage, and a daily job that saves snapshots so trends survive.

## How it works

```
browser ──▶ Express server ──▶ Salesforce REST API
                │
                ├── Postgres (daily snapshots)
                └── serves the built React app
```

The server exists for one reason. Vite inlines environment variables into the browser bundle, so a secret in the bundle is a published secret. All Salesforce calls happen server-side, and the browser only receives aggregates.

## Decisions worth explaining

- **Field names come from config.** Salesforce custom field names can't be guessed. I put them in environment variables and added discovery endpoints (`/objects`, `/describe/:object`), so the mapping can be checked against the org before anyone trusts a number.
- **Missing config produces a warning, not a wrong number.** If the "open" statuses aren't configured, the endpoint still answers but warns that closed records are included. Every query echoes the SOQL it ran.
- **The health check comes first.** `/api/sf/health` reports whether authentication works and which integration user it runs as, never the token. Every debugging session starts there.
- **The container port stayed on 80.** The platform's service targeted port 80 from the app's nginx days. A container on 8080 failed its readiness probe and restart-looped while the old pod kept serving the old build. I documented this in the README so nobody changes it back.
- **I split it when the audiences split.** Once Support and Revenue needed to move independently, I carved them into their own apps (projects 2 and 3) instead of growing one large `App.jsx`.

## Stack

React, Vite, Express, Salesforce REST (OAuth client credentials), Postgres, Docker.

## Talking points

- Moving from static snapshots to live reads without breaking the tabs people already used.
- Designing for a schema you don't control and can't see from the code.
