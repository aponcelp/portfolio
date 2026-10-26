# Comp and quota engine, plus an outbound engine

**Aug – Sep 2026 · Customer Success and Onboarding leadership**

## Problem

Customer Success quotas were typed in by hand, and nobody could explain where a number came from. The onboarding commission plan took hours to calculate each month, so specialists never saw their own pacing. Some of its measures also rewarded the wrong behaviour.

## What I built

One working prototype with a team switcher. Every rep gets one bar against the thing they have to clear, and clicking a row shows what's behind the number.

- **Customer Success quota.** Derived per CSM from data, never typed in, with every number showing its own arithmetic.
  - **Net upsell** comes from how the CSM's book has actually grown, recorded nightly from billing data. With no history yet, the tool uses a floor and labels it "provisional" instead of pretending.
  - **Retention** is a dollar amount: a target share of the revenue actually up for renewal that month.
  - **Pipeline credit** is the value sales puts on the opportunity, not the count of leads raised.
  - **A rotating campaign** completes the quota.
- **Two rule sets by segment.** Managed accounts are worked personally by a CSM. Smaller accounts are mostly worked by an AI outbound engine, so their campaign metric is meetings that reach the sales queue.
- **Onboarding commission.** A per-account window instead of a monthly book, with two KPIs only: engaged by day 90 (day 120 for larger accounts), and no early churn in the same window.
- **The outbound engine** for a plan migration: trigger evaluation, routing and sequences.

## Decisions worth explaining

- **A dollar retention target, not a save rate.** A save rate is easy to game by opening cancellation requests and saving most of them.
- **Measure engagement *at* day 90, not at first touch.** An account can cross the line on day 30 and fall back by day 70. Because the engagement measure swings with rent-collection timing, the tool stores a snapshot and refuses any reading outside a three-day window.
- **Pay flat at the window end, not in staggered tiers.** The old tiers pushed specialists toward accounts that would engage quickly and away from later go-lives.
- **Write down why measures were cut.** Removed measures and the reasons sit in the code, so nobody rebuilds them by accident.
- **No weight on missing data.** If nothing renews in a month, the retention component's weight moves to the others instead of scoring zero.
- **Split by book share, not evenly.** Books varied by more than 20×, so an even split would have been indefensible.

## How it's built

Node with zero runtime dependencies. Nightly snapshot jobs feed the history. Verification scripts check the live CRM and CS-platform mappings against a real account before the numbers are trusted. The app runs offline against an anonymised fixture, and 150 assertions cover the engines, the API and the rendered UI.

## Stack

Node, Postgres, CRM and customer-success-platform REST APIs, vanilla JS front end.

## Talking points

- Designing incentive plans that can't be gamed, and explaining every number.
- Point-in-time measurement for metrics that move with the calendar.
