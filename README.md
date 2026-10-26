# Alfredo Ponce de León — work at DoorLoop (2024 – 2026)

I was Director of Strategy & Operations for Customer Success at DoorLoop, a property management software company. Alongside running operations, I built the tools that Support, Onboarding and Customer Success ran on, designed the AI agents and automations behind them, and wrote the operating plans for leadership.

In my last year that came to about 9 deployed internal apps, 50+ interactive analyses and decision documents, and 10+ families of workflow automations.

This repo describes that work: the problem behind each piece, how I built it, and the decisions I would explain in an interview.

**There is no DoorLoop code or data in this repo.** The source code, documents and data belong to DoorLoop and stay there. Every page here was written from scratch. Any numbers are illustrative, and any screenshots use synthetic data.

## Apps

| # | Project | What it does | Stack |
|---|---|---|---|
| 1 | [CX Capacity Planner](projects/01-cx-capacity-planner.md) | Staffing and load planning for Onboarding and Customer Success, read live from Salesforce | React, Vite, Express, Salesforce REST, Postgres |
| 2 | [Churn and Revenue Forecast](projects/02-churn-revenue-forecast.md) | Forecasts where the month's churn will land, layer by layer, and scores every forecast once the month closes | Express, Salesforce SOQL, Postgres, React |
| 3 | [Support Capacity Planner and WFM](projects/03-support-capacity-planner.md) | Headcount needed for new support hours, plus schedule, live floor view and leaderboard | React, Express, Intercom API, Postgres, Slack API |
| 4 | [Support QA](projects/04-support-qa.md) | Monthly chat sampling, AI-assisted scoring and scorecards that feed coaching | React, Express, Intercom API, Postgres, n8n |
| 5 | [Support 1:1 Hub](projects/05-support-1on1-hub.md) | 1:1 notes, action items and QA targets with role-based access | Node, Express, Postgres, Google OAuth |
| 6 | [Website Studio](projects/06-website-studio.md) | One board for the customer website pipeline, with AI first drafts of site copy | Node, Express, Salesforce, Claude API |
| 7 | [Customer Commander](projects/07-customer-commander.md) | Prototype of the CSM workspace for an AI agent system: book, 2×2 portfolio, agent tasks, playbooks ranked by results | React, TypeScript, Tailwind, Recharts |
| 7b | [Onboarding Commander](projects/07b-onboarding-commander.md) | The onboarding sibling: daily must-dos by role, activation 2×2, customer-facing success plans, agent library | React, TypeScript, Tailwind, Recharts |
| 8 | [CSM bonus dashboard (contributions)](projects/08-csm-bonus-dashboard.md) | My changes to a teammate's dashboard: churn rules, activity minutes, deploy pipeline | Next.js, Salesforce, GitHub Actions |
| 9 | [Onboarding Cadence App](projects/09-onboarding-cadence-app.md) | Weekly onboarding KPIs with a Monday agenda that shows only what deserves discussion | Node, Express, Postgres |
| 10 | [Success Plan Generator](projects/10-success-plan-generator.md) | AI-personalised, customer-facing onboarding plans from account data and specialist notes | Vanilla JS, Express, Claude API |
| 11 | [Training, webinar and campaign-link tools](projects/11-training-and-webinar-dashboards.md) | Training-site analytics, a webinar funnel and a UTM link builder | Express, Chart.js, PostHog, Livestorm |

## Beyond the apps

| # | Area | What it covers |
|---|---|---|
| 12 | [AI agents and automations](projects/12-ai-agents-and-automations.md) | Agent contracts, a refinement board, and 10+ n8n automation families |
| 13 | [Analysis and live dashboards](projects/13-analysis-and-dashboards.md) | Retention deep dives, trend-or-anomaly checks, operations metrics, research tools |
| 14 | [Strategy and operating design](projects/14-strategy-and-operating-design.md) | Operating models, executive reviews, data contracts, risk redesign, competitive research |

## How I build

These patterns show up across the work:

- **Answer first.** Each page opens with the number a manager needs. The reasoning is one click away: every forecast layer, score and headcount figure opens into its arithmetic.
- **Secrets stay on the server.** Browser bundles get aggregates, never credentials. Integrations run as service accounts with the least access the tool needs.
- **Say when a number is weak.** If a filter isn't configured or a source is missing, the API returns a warning and the page shows it. It doesn't return a confident wrong number.
- **Match the source system.** When people compare my numbers with Intercom's or Salesforce's own reports, the definitions have to match. I replicated report definitions and checked them against real values before calling a tool done.
- **Rules before agents.** Make the process visible and the rules explicit, then automate the checklist. Agents prepare evidence, and a person decides where money, risk or pay is involved.
- **Read-only first, writes later.** New tools start by reading. Every write to another system is a button a person presses, added once that system's owner agrees.
- **Built for handoff.** Config lives in environment variables, not code. There's a health endpoint that says exactly what's missing, a README written for the next owner, and tests for the parts that hold logic.

## Tools I used

JavaScript and TypeScript, React, Vite, Node and Express, Next.js, PostgreSQL (with pg-mem and PGlite for local runs), Supabase, SQLite, Python, Salesforce REST and SOQL, Intercom API and reporting exports, Slack API, Google OAuth, PostHog, n8n, the Claude API, Docker, GitHub Actions, and an internal Kubernetes deploy platform. I did most of the building in Claude Code.

## Screenshots

[`screenshots/`](screenshots/) holds images of each tool running on synthetic data only.
