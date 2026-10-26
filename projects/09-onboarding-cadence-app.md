# Onboarding Cadence App

**Aug 2026 · Onboarding and Implementation leadership**

## Problem

The weekly onboarding review ran on per-rep tables in a notes tool. Nobody could sort, compute or compare them. Each Monday meeting walked through every number instead of the few that mattered.

## What I built

A small app for the weekly KPI cadence:

1. **Enter**: segment owners fill the week's grid, 17 metrics per segment. Cells autosave, and the keyboard moves down a column. A bulk-paste option takes a block copied from a dashboard.
2. **Submit**: one button per week, which unlocks insights and comparisons.
3. **Read**: an agenda for Monday that lists only what deserves discussion.
4. **Edit any time**: later edits re-run the analysis and are logged, so "this number changed after we submitted" can be checked instead of argued about.

## Decisions worth explaining

- **Two thresholds, because they do different jobs.** A ±5 move colours a cell. Only a ±10 move earns a place on the agenda.
- **Compare reps with their peers, not with the target.** On most funnel metrics the whole sub-team is below target, so that's a team story. The agenda flags reps 10+ points from their own sub-team's median, in either direction: "why is this bad" and "why is this good, so we can copy it".
- **Know which direction is good.** For metrics like days out, share of accounts with no touchpoints, or cancellation rate, down is good.
- **Suppress low volume.** A percentage based on fewer than 10 accounts stays off the agenda and out of the median, because 100% of one account isn't a signal.
- **Respect cohort maturity.** Cohort metrics only compare month to month at equal maturity, and warn instead of asserting.
- **Add context instead of filtering.** A rep who was out or inherited a book keeps their numbers, with the reason shown next to them.

## Stack

Node, Express, Postgres, Docker, and a Node test suite covering logic, empty states and smoke tests.

## Talking points

- Designing a meeting agenda as a filter: what not to show matters as much as what to show.
- Statistical guardrails that a non-technical team can follow.
