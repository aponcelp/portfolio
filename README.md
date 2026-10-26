# Alfredo Ponce de León — work at DoorLoop (2026)

I worked on the Customer Experience team at DoorLoop, a property management software company. During 2026 I built the internal tools that Support, Onboarding and Customer Success ran on: capacity planning, revenue forecasting, workforce management, QA, 1:1s and a website pipeline.

This repo describes that work: the problem behind each tool, how I built it, and the decisions I would explain in an interview.

**There is no DoorLoop code or data in this repo.** The source code belongs to DoorLoop and stays in its repositories. Every page here was written from scratch. Any numbers are illustrative, and any screenshots use synthetic data.

## Projects

| # | Project | What it does | Stack |
|---|---|---|---|
| 1 | [CX Capacity Planner](projects/01-cx-capacity-planner.md) | Staffing and load planning for Onboarding and Customer Success, read live from Salesforce | React, Vite, Express, Salesforce REST, Postgres |
| 2 | [Churn and Revenue Forecast](projects/02-churn-revenue-forecast.md) | Forecasts where the month's churn will land, layer by layer, and scores every forecast once the month closes | Express, Salesforce SOQL, Postgres, React |
| 3 | [Support Capacity Planner and WFM](projects/03-support-capacity-planner.md) | Headcount needed for new support hours, plus schedule, live floor view and leaderboard | React, Express, Intercom API, Postgres, Slack API |
| 4 | [Support QA](projects/04-support-qa.md) | Monthly chat sampling, AI-assisted scoring and scorecards that feed coaching | React, Express, Intercom API, Postgres, n8n, LLM grader |
| 5 | [Support 1:1 Hub](projects/05-support-1on1-hub.md) | 1:1 notes, action items and QA targets with role-based access | Node, Express, Postgres, Google OAuth |
| 6 | [Website Studio](projects/06-website-studio.md) | One board for the customer website pipeline, with AI first drafts of site copy | Node, Express, Salesforce, Claude API, Postgres |
| 7 | [CX Agent System prototypes](projects/07-agent-system-prototypes.md) | Clickable prototypes that showed CSMs and Onboarding how an AI agent system would work | React, TypeScript, Tailwind, Recharts |
| 8 | [CSM bonus dashboard (contributions)](projects/08-csm-bonus-dashboard.md) | My changes to a teammate's dashboard: churn rules, activity minutes, deploy pipeline | Next.js, Salesforce, GitHub Actions, GHCR |

## How I build

These patterns show up in every project:

- **Answer first.** Each page opens with the number a manager needs. The reasoning is one click away: every forecast layer, score and headcount figure opens into its arithmetic.
- **Secrets stay on the server.** Browser bundles get aggregates, never credentials. Integrations run as service accounts with the least access the tool needs.
- **Say when a number is weak.** If a filter isn't configured or a source is missing, the API returns a warning and the page shows it. It doesn't return a confident wrong number.
- **Match the source system.** When people compare my numbers with Intercom's or Salesforce's own reports, the definitions have to match. I replicated report definitions and checked them against real values before calling a tool done.
- **Read-only first, writes later.** New tools start by reading. Every write to another system is a button a person presses, added once that system's owner agrees.
- **Built for handoff.** Config lives in environment variables, not code. There's a health endpoint that says exactly what's missing, a README written for the next owner, and tests for the parts that hold logic.
- **AI where it saves time, a person where it matters.** LLMs draft website copy and pre-score QA chats. A person approves anything that reaches a customer or affects pay.

## Tools I used

JavaScript and TypeScript, React, Vite, Node and Express, Next.js, PostgreSQL (with pg-mem and PGlite for local runs), Salesforce REST and SOQL, the Intercom API including its reporting exports, Slack API, Google OAuth, n8n, the Claude API, Docker, GitHub Actions, and an internal Kubernetes deploy platform. I did most of the building in Claude Code.

## Screenshots

[`screenshots/`](screenshots/) holds images of each tool running on synthetic data only.
