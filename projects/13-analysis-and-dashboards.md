# Analysis and live dashboards

**2026 · CX and executive leadership**

Most of my analysis shipped as interactive pages rather than slides. Each one leads with the answer and keeps the method one click away. They are listed here by the question they answered; the pages themselves stay with DoorLoop because they contain company data.

## Retention

- **Monthly retention deep dives**: what drove the month's churn, broken down so leadership could see the accounts behind each figure.
- **Trend or anomaly?** Is a month's change a real trend or noise? It compares against seasonality and the usual spread before anyone reacts.
- **One feed, two tenures.** The same signals read differently for new and long-standing customers, so the review split at 90 days.

## Operations metrics

- **CX metrics tracker**: one page for the recurring CX numbers, with definitions.
- **Onboarding SLA dashboard**: SLA breaches week over week, backed by a small database.
- **Chat volume by week of month**: when demand actually arrives, which fed staffing.
- **Onboarding sessions per account**: how much onboarding customers really receive, by segment.
- **Rep performance, inbound calls and funnel dashboards**: local live pages refreshed from source systems.

## Research tools

- **Call-transcript scan**: a script that searched call recordings for specific mentions and summarised the findings.
- **Account snapshots**: a point-in-time export of accounts into one file per account plus a database, so an AI assistant could answer questions about the book without live access.
- **Weekly sprint readout**: an automatically written summary of the CX Ops sprint, drafted by a small model.

## Decisions worth explaining

- **The answer goes in the headline.** The first line of each page is the conclusion, not "this page shows".
- **Show the accounts behind the number.** A churn figure leadership can click into gets trusted, and acted on, faster.
- **Separate the trend from the noise first.** That step saved a lot of reactions to ordinary months.

## Stack

Claude artifacts (HTML, JS, charts), Python, SQLite, Supabase, CRM and analytics APIs.
