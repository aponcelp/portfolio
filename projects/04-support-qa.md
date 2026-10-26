# Support QA

**Oct 2026 · Support leads and reviewers**

## Problem

QA scores were about to count toward rep compensation and drive training. Reviews were manual and the sample wasn't consistent.

## What I built

An app that follows the monthly QA cycle:

1. **This month**: pick the month and the number of chats per rep. Chats that match an "always review" rule go first (up to half the sample), and the rest are random.
2. **Review**: one chat at a time, with AI suggestions pre-filled. The reviewer accepts or changes each line, then saves and moves to the next.
3. **Team**: scores per rep by month and year, a check against the minimum score, and a rep page with the weakest scorecard lines and reviewer notes for 1:1s.
4. **Settings**: who is in QA, a versioned scorecard, the review rules and the minimum score.

## How it works

- Chat text is fetched from Intercom on demand and **never stored**. Only conversation IDs, scores, short quotes and reviewer notes are saved.
- Scoring goes to an n8n workflow owned by another team, through an adapter that maps its output onto the app's scorecard.
- The final score on each line is the reviewer's if present, otherwise the AI's.

## Decisions worth explaining

- **No fake scores on real chats.** Without a live scorer, real chats are left unscored for a person. Demo scores only appear on demo chats.
- **Adapt to the grader rather than fork it.** The rubric lives in one place, the n8n workflow, and the app follows it. If the grader's criteria change, the app changes in one mapping.
- **Store as little as possible.** Pay-relevant data deserves minimal retention and access control before real use.

## Stack

React, Vite, Express, Intercom API, Postgres (PGlite locally), n8n webhook grader, Docker.

## Talking points

- Designing AI-assisted review where a person stays accountable.
- Data minimisation for sensitive, pay-related records.
