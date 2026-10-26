# Support 1:1 Hub

**Oct 2026 · Support leads and reps**

## Problem

1:1 notes and action items lived in scattered docs. Leads couldn't see a rep's history in one place, and the tool needed a backend so it could later pull QA and leaderboard numbers automatically.

## What I built

A web app with three levels of access:

- **Leads** run 1:1s, see every rep and set QA targets.
- **Admins** have the same access as leads.
- **Reps** see only their own 1:1s and can tick their own action items.
- Anyone else at the company gets a "not on the roster" page.

## How it works

- Google sign-in limited to the company domain, checked on both the hosted-domain claim and the email.
- A signed session cookie (12 hours). Access is re-checked against the roster on every request, so archiving a rep cuts access immediately.
- The roster is seeded once from a file, then managed in the app.
- `/healthz` reports whether OAuth, the session secret and the database are configured.
- A local dev sign-in route and an in-memory database let anyone run it without Google credentials.

## Decisions worth explaining

- **Google sign-in instead of the platform gate.** The deploy platform's gate didn't pass the viewer's identity to the app, and role-based access needs to know who is viewing.
- **Check the roster on every request.** That's slightly more database work, but removing someone takes effect at once.
- **Roles from config.** Leads and admins are environment variables, so a new owner can change them without a code change.

## Stack

Node, Express, Postgres (pg-mem locally), Google OAuth 2.0, vanilla JS front end, Docker.

## Talking points

- Moving a prototype from a shared document to a real app with authentication.
- Debugging OAuth in production from logs alone (an `invalid_client` traced to a mistyped secret).
