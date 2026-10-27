# Well Run

**Oct 2026 – present · Personal build · [wellrun.so](https://www.wellrun.so)**

## Problem

I wanted to know how startups are really doing, and whether they look built to last. Funding news tells you who raised money. It doesn't tell you who is still hiring, growing and moving a year later. I couldn't find one place that put those signals side by side, so I built it.

## What I built

A public scoreboard of 600+ startups, ranked on execution and re-ranked every week.

1. **A score from public signals.** Each company earns points for hiring (open roles across the whole team), how recent its last funding round is, and traction (revenue, customer and headcount growth). Recent red flags, like layoffs, take points away.
2. **A race theme.** I'm a big sports fan, so the score maps to a running pace. Companies sit in zones from Sprint to Cool-down, and a separate distance measure shows market position, from a 10K to a marathon.
3. **The Well Run 100 and a weekly chart.** The board re-ranks every Sunday. The chart shows each company's rank this week and last week, its peak, and how many weeks it has held a top-100 spot.
4. **A page per company.** Founders, funding history, news, hiring history, rivals, and the arithmetic behind its score.
5. **Well Run Weekly.** A newsletter on Beehiiv, written as a short letter from me about one story in the data each week.

## Decisions worth explaining

- **Public signals only.** Every input comes from a public source. That leaves out some useful data, but anyone can check a score.
- **Missing data stays neutral.** A company with no public revenue figure isn't punished for it. Otherwise the board would reward companies that publicize, not companies that execute.
- **A fresh round isn't execution.** A seed or small Series A without real traction starts in Warm-up, whatever its score.
- **Show the arithmetic.** Each company page explains how its score was built. If a number looks wrong, a reader can see why.
- **Let readers' behavior pick the next feature.** Analytics show which companies get opened, which filters get used, and what people search for and don't find. Missed searches feed the list of companies to add. When I saw visitors from Google read one company page and leave, I added a section pointing to the companies around it.
- **Keep real history.** Data lives in a database with a snapshot every week, so rank history is recorded, not reconstructed. A GitHub Action posts a summary of every board change: adds, removals and zone moves.

## How I built it

On my own, with AI agents (Hark) doing most of the research and code while I made the calls on scoring, curation and design. It started on Oct 11, 2026 as a single static page with 34 companies, and moved to Next.js with a page per company eight days later.

## Stack

Next.js, Supabase, Vercel, GitHub Actions, PostHog, Sentry, Beehiiv.

## Talking points

- Turning a fuzzy question ("is this company doing well?") into a score people can argue with.
- Scoring rules that hold up when data is missing or noisy.
- Shipping in public, then using real behavior to decide what to build next.
