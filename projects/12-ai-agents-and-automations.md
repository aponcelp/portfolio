# AI agents and automations

**2026 · Onboarding, Customer Success, Support and GTM operations**

Besides the apps, I designed AI agents and ran a set of workflow automations in n8n, working with an automation engineer I hired. My approach had a simple rule: **rules before agents**. First make the process visible and the rules explicit, then automate the checklist, and only then let an agent take an action.

## Agent design

- **Agent contracts.** I wrote short contracts that state what an agent may read, decide and do, what it must hand back to a person, and how it's measured. For onboarding there was a compact contract the agent loads, backed by a longer blueprint of the role.
- **A refinement board.** Each agent's known failure modes and fixes were tracked in one place and reviewed by lane, so quality improved on a schedule instead of by complaint.
- **Agents I specified**:
  - an onboarding call-coverage agent (are the right modules covered on calls?)
  - a verification agent that prepares a risk reviewer's checklist without making the decision
  - playbook and upsell engines that choose the next action for an account
- **Prototypes** of the agent system for CSMs and onboarding ([project 7](07-agent-system-prototypes.md)).

## Automation families

I ran these in a shared n8n workspace. Authorship per workflow wasn't always recorded, so this is the CX and GTM operations side I owned or drove.

| Family | What it does |
|---|---|
| Onboarding agents as tools | Assigns an onboarder, prepares kickoffs, checks text, tracks onboarder capacity |
| Coaching and scoring | Implementation, training and onboarding coaches with daily and weekly digests |
| Support QA pipeline | Random conversations scored by AI, with results saved for the QA app ([project 4](04-support-qa.md)) |
| System syncs | Risks, expansions, cancellation requests and escalations kept in sync across support inbox, CRM and CS platform |
| Cancellation intake | Support-inbox cancellation requests into the CRM. Replaced two older automations, with a watchdog |
| Autofill from calls | Call recordings into onboarding and CS events, modules covered and account notes |
| Availability alerts | Booking-calendar capacity trackers with threshold alerts |
| Insight digests | Risk and sentiment, pain points, weekly CS digest, feature mentions from calls |
| Voice of customer | Nightly feature requests from support into the product backlog |
| Ops plumbing | Request processor, error intake, execution-usage monitor, risk alerts |

## Decisions worth explaining

- **Automate the checklist, not the judgment.** Agents prepare evidence, and a person decides where money, risk or pay is involved.
- **Replace an automation only with something observable.** New workflows came with a watchdog or an error intake, so a silent failure showed up.
- **Choose where to build.** I wrote a simple rubric for when something should be an n8n workflow, a small app, or a request to engineering.

## Stack

n8n, LLM APIs, CRM, support-inbox and call-recording APIs, MCP tools.
