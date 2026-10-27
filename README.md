# Alfredo Ponce de León — portfolio

## About

I'm an operations leader based in Miami. My work sits across business operations, customer and post-sale strategy, and product ops and AI deployment. I like taking a problem nobody owns yet, putting structure around it, and building the system, team or tool that fixes it.

This repo shows that work in three parts: what I built at DoorLoop, case studies from interviews, and two things I built on my own. More about me is on [my profile](https://github.com/aponcelp).

## Start here

Short on time? These four show the range best:

1. [Churn and Revenue Forecast](projects/02-churn-revenue-forecast.md): a layered forecast that scores itself once each month closes.
2. [Customer Commander](projects/07-customer-commander.md): a prototype of the CSM workspace for an AI agent system.
3. [AI agents and automations](projects/12-ai-agents-and-automations.md): agent contracts, a refinement board, and 10+ automation families.
4. [Well Run](projects/21-well-run.md): a public ranking of 600+ startups on execution, re-ranked every week.

## Work at DoorLoop (2024 – present)

I'm the GTM Strategy & Operations Manager at DoorLoop, a property management software company. Alongside running operations, I built the tools that Support, Onboarding and Customer Success ran on, designed the AI agents and automations behind them, and wrote the operating plans for leadership.

Over the past year that has come to more than 10 deployed internal apps, 50+ interactive analyses and decision documents, and 10+ families of workflow automations.

This section describes that work: the problem behind each piece, how I built it, and the decisions I would explain in an interview.

**There is no DoorLoop code or data in this repo.** The source code, documents and data belong to DoorLoop and stay there. Every page here was written from scratch. Any numbers are illustrative, and any screenshots use synthetic data.

### Apps

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
| 16 | [Comp and quota engine](projects/16-comp-and-quota-engine.md) | CS quotas derived from book data, an onboarding commission measured at day 90, and an AI outbound engine | Node, Postgres, CRM APIs |

### Beyond the apps

| # | Area | What it covers |
|---|---|---|
| 12 | [AI agents and automations](projects/12-ai-agents-and-automations.md) | Agent contracts, a refinement board, and 10+ n8n automation families |
| 13 | [Analysis and live dashboards](projects/13-analysis-and-dashboards.md) | Retention deep dives, trend-or-anomaly checks, operations metrics, research tools |
| 14 | [Strategy and operating design](projects/14-strategy-and-operating-design.md) | Operating models, executive reviews, data contracts, risk redesign, competitive research |

### How I build

These patterns show up across the work:

- **Answer first.** Each page opens with the number a manager needs. The reasoning is one click away: every forecast layer, score and headcount figure opens into its arithmetic.
- **Secrets stay on the server.** Browser bundles get aggregates, never credentials. Integrations run as service accounts with the least access the tool needs.
- **Say when a number is weak.** If a filter isn't configured or a source is missing, the API returns a warning and the page shows it. It doesn't return a confident wrong number.
- **Match the source system.** When people compare my numbers with Intercom's or Salesforce's own reports, the definitions have to match. I replicated report definitions and checked them against real values before calling a tool done.
- **Rules before agents.** Make the process visible and the rules explicit, then automate the checklist. Agents prepare evidence, and a person decides where money, risk or pay is involved.
- **Read-only first, writes later.** New tools start by reading. Every write to another system is a button a person presses, added once that system's owner agrees.
- **Built for handoff.** Config lives in environment variables, not code. There's a health endpoint that says exactly what's missing, a README written for the next owner, and tests for the parts that hold logic.

### Tools I used at DoorLoop

JavaScript and TypeScript, React, Vite, Node and Express, Next.js, PostgreSQL (with pg-mem and PGlite for local runs), Supabase, SQLite, Python, Salesforce REST and SOQL, Intercom API and reporting exports, Slack API, Google OAuth, PostHog, n8n, the Claude API, Docker, GitHub Actions, and an internal Kubernetes deploy platform. At DoorLoop, I did most of the building in Claude Code.

## Case studies

Case work from interviews, written from scratch. Except for Ambrook, company names are left out, and none of the pages reproduce a company's materials or data.

| # | Case | What it covers |
|---|---|---|
| 15 | [Farm starting balances (Ambrook)](projects/15-case-ambrook-starting-balances.md) | Product Operations take-home: why balance sheet setup goes wrong, and an AI-plus-rules review pipeline to fix it |
| 17 | [SMB onboarding in one week](projects/17-case-onboarding-speed.md) | Customer operations case: why onboarding took two months, and a readiness, starter-pack and first-week plan to get it to five days |
| 18 | [Territory-based lead routing](projects/18-case-territory-routing.md) | RevOps take-home: moving a sales team from a national round robin to state territories without breaking trust in lead distribution or pay |
| 19 | [Profile quality metric](projects/19-case-profile-quality-metric.md) | Revenue strategy take-home: what makes a marketplace profile book fast, turned into a gate, a score and a comp change |
| 20 | [Customer revenue retention model](projects/20-case-revenue-retention-model.md) | Customer ops take-home: an ARR snowball, retention dashboard and forecast showing one segment's expansion hiding churn in the others |

## Personal builds

Built on my own time with AI agents (Hark). No DoorLoop code or data.

| # | Project | What it does | Stack |
|---|---|---|---|
| 21 | [Well Run](projects/21-well-run.md) | Ranks 600+ startups on execution from public signals, re-ranked weekly, with a page per company and a weekly newsletter. Live at [wellrun.so](https://www.wellrun.so) | Next.js, Supabase, Vercel, GitHub Actions, PostHog, Sentry, Beehiiv |
| 22 | [Job search operating system](projects/22-job-search-os.md) | My own ops playbook run on my job search: a private tracker with focus plays, tasks and a résumé library, fed by a daily radar of job boards | HTML/JS, Supabase, Vercel, Google Sheets API, Python |

## Screenshots

[`screenshots/`](screenshots/) holds images of the DoorLoop tools running on synthetic data only.

