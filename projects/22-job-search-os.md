# Job search operating system

**Oct 2026 – present · Personal build**

## Problem

A senior job search is an operations problem. Hundreds of companies, a few dozen live roles, tailored résumés, follow-ups, and interviews at different stages. I was running it across a spreadsheet, my inbox and a folder of résumés, and I kept losing track of what came next.

So I ran my own playbook on it: one source of truth, a short list of priorities, and a daily cadence.

## What I built

A private tracker app, plus the automation that keeps it fed.

1. **Today.** The day's tasks and my focus plays: a short list of priority roles, each with its next move.
2. **Pipeline.** Every role with a priority, from "interview this week" to "closed", plus its stage and next step.
3. **New roles.** A daily radar scans company job boards on Ashby, Greenhouse, Lever, Gem and Workable, plus a few job sites. It filters by role, level, location and company stage, and new matches land here. One click adds a role to the pipeline.
4. **Résumés.** A library of tailored versions, each with a code, so I always know which résumé went to which company.
5. **To-do, contacts and progress.** Open tasks, the people I know at each company, and a view of how the search is moving.

## Decisions worth explaining

- **One source of truth, two ways in.** The app and a Google Sheet sync both ways. If I edited a role in the app since the last sync, the app wins. If only the sheet changed, the sheet wins. Nothing gets overwritten silently.
- **Fewer things, done better.** The pipeline holds a lot of roles. The app puts a short list in front of me each day, because a search moves on a few good conversations, not on the number of applications.
- **Wide radar, strict filters.** The scans cover hundreds of companies, then cut hard: Miami or US remote, the right level, and the kind of companies I want to work for. A match is checked against the live posting before it shows up.
- **The app never acts for me.** It doesn't send messages or submit applications. Drafts get ready; I decide and I send.
- **Private by design.** Sign-in is an email link for a single account, and every table is locked to that account with row-level security. The code holds no personal data: no pipeline, no contacts, no résumés.

## How I built it

With AI agents (Hark). They wrote the app, the scans and the sync, and they run the daily radar. I set the rules: which roles count, what a good fit looks like, and what makes the focus list.

## Stack

HTML and JavaScript (no framework), Supabase (Postgres, auth, row-level security), Vercel, Google Sheets API, Python for the board scans and the sync.

## Talking points

- Running an operating cadence on a personal problem: one tracker, a short priority list, a daily radar.
- Sync rules that decide who wins when two systems disagree.
- Automating the research and the bookkeeping, and keeping every decision with a person.
