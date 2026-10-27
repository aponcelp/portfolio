# Case study: SMB onboarding from two months to one week

**Oct 2026 · Case presentation, customer operations · 30-minute presentation plus panel Q&A**

The company makes operations software for property managers. The case came with an export of recent small-business onboardings and four questions: where the time goes, what the data suggests, how to get onboarding down to about eight hours of hands-on work, and how to prove it. The company, its data and the prompt text aren't reproduced here.

## The goal I set

New SMB customers fully onboarded in five business days, with about eight hours of hands-on time across the customer and our team.

I read "eight hours" as total hands-on time over the first week, not one long day. Nobody can give us eight hours straight. I said that up front, because it shapes everything after it.

## What I found

Before anything else I cleaned the export. It had a duplicate account, a test account with every date on the same day, and one account too big to count as SMB.

- **Most of the time is waiting.** Onboarding took close to two months, and very little of it was work. Every step waited for the one before it. More than a week passed before the kickoff call, with no setup happening.
- **One integration is the bottleneck.** Connecting the customer's property management system took about a third of all onboarding time. The connection itself is a few self-serve steps, so that time was waiting, mostly on the customer's admin.
- **That step is also where accounts are lost.** Almost every stalled account got stuck around it, and none of the stalled accounts renewed.
- **Two levers worked, each on its own step.** When Sales collected integration details before close, the connection happened much faster. When customers used a starter template pack, workflows and templates went live much faster, and fewer accounts stalled. Each lever moved only the step it should touch. That's why I believed the effect was real, even with small groups. If it were just better customers, everything would speed up.
- **Customers pay while they wait.** Public reviews said billing starts on day one, live or not. Every day of waiting is a renewal risk.
- **Size isn't the cause.** Smaller and larger SMB accounts took about the same time.

## What I proposed

1. **Readiness before close.** Sales asks three questions on the closing call: which system they use, who has the admin login, and whether their plan allows integrations. No credentials before signing. The CRM won't let a deal close until those answers, a setup owner and a booked kickoff are in. At signature, the admin gets the connect guide for their system.
2. **A starter pack per type of operation.** Workflows, checklists, templates and the customer's expected first week. It starts as content. Later, Product pre-builds it into new accounts, and the pilot results make that case.
3. **A first-week model with steps in parallel.** Only a couple of steps actually need the integration. Checklists, team invites, the mobile app and workflow setup can all start on day one. Kickoff within one business day of signing, two short 1:1 sessions (90 and 60 minutes), and nudges in between. No block longer than 90 minutes.

How it runs day to day: every milestone has a due day, and accounts are checked daily. A missed day triggers a nudge first, then an alert to the owner with context and a suggested action. If more than 10% of active accounts fall off the path in a week, the problem is the process, not the accounts.

## How I'd prove it

A pilot of all three changes together, on the next ~20 new SMB accounts with a self-serve integration. One onboarding specialist runs it, a second shadows, and two or three Sales reps take part. Compare against the same specialist's earlier accounts and other specialists' accounts from the same weeks.

- **Headline:** time to value, from signature to the first task created from a real reservation. Target: five business days.
- **Guardrail:** accounts off the ideal path, under 10% a week.
- **Lagging:** year-one renewal, with 90-day active use as the early read.

## What I'd point out

- **Readiness, not credentials.** Asking for logins before signing is a privacy problem and slows down short sales cycles. Three questions and a connect guide do the same job.
- **Keep the 1:1 time for now.** Remove it later, once we know where customers actually get stuck.
- **Speed and renewal move together, but that's not proof.** Faster customers might just be better customers. The pilot tests the cause.
- **Rules before agents.** Nudges, alerts and a risk score inform and recommend. An agent can draft follow-ups, and the specialist decides.
- **How I used AI.** Claude Code cleaned the data, built the charts and checked my numbers. I corrected it where it went wrong: it wanted to collect credentials before close, and it read eight hours as one day. The recommendations were mine.

## Tools

Python for cleaning and charts, Claude Code, a written plan with a day-by-day first week and a milestone table.
