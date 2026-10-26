# Support Capacity Planner and WFM

**Oct 2026 · Support leadership and the support floor**

## Problem

Support was extending its hours to evenings and weekends. Leadership needed to know how many people that would take, by channel and by hour. The floor also ran its schedule in a separate tool, and agents didn't trust the existing performance numbers.

## What I built

One app with six tabs:

- **Plan**: people needed for the new hours, built step by step: volume, expected growth, minutes per contact, what one person delivers, arrivals by hour, shifts, then 5-day weeks and PTO. A 13-month projection uses demand per customer, customer growth, trend, seasonality and an automation ramp. Only contacts the AI bot doesn't resolve reach a person.
- **Coverage**: need against the people on the floor, hour by hour.
- **Schedule**: an 8-week schedule in Postgres. Managers mark sick, PTO, training, channel changes and weekend shifts. Changing a regular shift updates future days and leaves manually edited days alone. Every change is logged and can send the agent a Slack DM.
- **Floor**: who is working right now, from schedule plus live status.
- **Leaderboard**: a podium, then everyone, ranked within each squad. Each score opens into its parts.
- **CSAT**: on its own tab, kept out of capacity math on purpose.

## How it works

The server reads Intercom in the background into an ID-keyed store and saves it to a Postgres cache. After a restart, data is back in about a second instead of a ten-minute re-read.

## Decisions worth explaining

- **Match Intercom's own reports.** The team lead noticed leaderboard numbers didn't match Intercom's dashboards. I rebuilt the counts on Intercom's reporting export, with the same definitions of "closed", "replied", first response and CSAT. I checked one agent's month against Intercom until the figures matched within a few units. I streamed the export, because buffering it ran the 512 MB container out of memory.
- **The score is percentiles, not raw counts.** Each measure is a percentile among comparable agents, with weights. Volume is shown but not scored, and a measure with no data drops out so the other weights rescale. Chat and phone agents are ranked separately, because comparing them wasn't fair.
- **Explain every number.** After feedback that the first version was confusing, I redesigned it: answer-first tabs, a "?" and a "How to read this" on every card, and assumptions shown as chips with tooltips.
- **Name the constraint you found.** The data showed rep-answered calls stopped before phone shifts ended. That was a routing setting to fix before adding evening phone staff, not a reason to hire more.

## Stack

React, Vite, Express, Intercom REST and reporting export APIs, Postgres (pg-mem locally), Slack Web API, Docker.

## Talking points

- Turning a staffing question into a model a non-technical manager can follow line by line.
- Earning trust in metrics by reproducing the source system's definitions exactly.
