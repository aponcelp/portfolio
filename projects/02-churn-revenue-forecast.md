# Churn and Revenue Forecast

**Sep – Oct 2026 · CX and finance leadership**

## Problem

Leadership wanted to know early where the month's churn would land. The existing report listed "pending" cancellations but missed several kinds of churn, and nobody checked whether past forecasts had been right.

## What I built

A forecast that builds the month from layers, ordered from counted to estimated:

1. **Scheduled cancellations**: already on the books.
2. **Open cancellation requests × outcome rate**: requests in flight, weighted by how often they actually churn.
3. **Requests not filed yet**: the expected rest of the month, from historical pace.
4. **Involuntary churn**: failed payments.
5. **Broken saves**: accounts saved earlier that cancel anyway.
6. **Annual renewals** due in the window.

Each layer opens into its arithmetic. Beside the model are:

- **At the usual pace**: a second read that uses only the calendar (what share of a month's churn has usually landed by this day).
- **The existing report's definition, replicated** status by status, so the gap between the two is visible.
- **Early churn**: 90-day churn per signup cohort, with the curve fitted separately per billing interval.
- **Forecast vs actual**: every daily projection is saved and scored once its month closes.

## How it works

All rates are measured from Salesforce at run time over a rolling 13-month window, with recent months weighted more heavily and seasonal effects damped. A daily job writes a snapshot to Postgres, which feeds the scoring.

## Decisions worth explaining

- **Count before you estimate.** Leading with the most certain layers made it obvious when an estimated layer was doing too much of the work.
- **Debug with diagnostics, not guesses.** The first version undercounted. I added a diagnostic endpoint that listed the accounts the model could and couldn't see. It found two causes: a status filter that dropped scheduled cancellations, and test accounts distorting one month. Both were fixed at the query, not patched in the output.
- **Score yourself.** Without the forecast-vs-actual table, nobody would know whether to trust the number.
- **A handoff doc.** I wrote a document covering the data mapping, the model and every bug fixed, so the next owner doesn't need me.

## Stack

Express, Salesforce SOQL, Postgres, React, Vite, Node test runner.

## Talking points

- Breaking a single forecast into explainable layers.
- Replicating an existing report to earn trust before replacing it.
