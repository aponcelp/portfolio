# Onboarding Success Plan Generator

**Jul 2026 · Onboarding specialists**

## Problem

Each new customer should get an onboarding plan that fits their situation. Writing one by hand took too long, so most customers got a generic one.

## What I built

A tool that turns an account into a branded, customer-facing onboarding plan:

- **Load the account** by live search from the customer success platform, a CSV export, or manual entry.
- **A setup snapshot** of the account's current usage, shown before generating.
- **AI personalisation.** The specialist adds free-text notes, for example "nervous about migrating, wants weekly calls". An LLM works those notes and the signup answers into tailored goals, flagged priority modules and a short note from the onboarding team.
- **The plan itself**: a go-live countdown, "what success looks like" in the customer's own terms, the first two steps with due dates, a three-stage roadmap, optional modules matched to the customer's interests, meeting cadence and a booking link.
- **Output** to print, to email HTML, or straight into the account's conversation composer.

## Decisions worth explaining

- **The specialist's notes drive the personalisation.** The AI works from what a person observed, not only from CRM fields.
- **Several ways to load an account.** The tool works even when the live integration doesn't.
- **The API key stays on the server.** A small Express proxy holds it.

## Stack

Vanilla JS front end with no build step, Express proxy, a customer success platform's REST API, Claude API.
