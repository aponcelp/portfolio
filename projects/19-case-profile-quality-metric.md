# Case study: defining and paying for profile quality

**Sep 2026 · Take-home case, revenue strategy and insights · Written memo plus an analysis workbook**

A healthcare marketplace's sales reps recruit providers and get them live, but there was no shared standard for what a good marketplace profile looks like, and quality varied widely by rep. Using a dataset of provider profiles and booking outcomes, I was asked to find what drives a fast first booking, turn it into a metric reps are held to, and say what tools I'd build. The company, its data and the prompt text aren't reproduced here.

## My approach

**Pick the outcome before judging the inputs.** The funnel has two milestones: going live and booking a first patient. Going live wasn't the problem; nearly every provider got there. The real drop-off came after: a large share never booked at all, and almost every booking that would ever happen had happened within 30 days of going live. So I used "booked within 30 days" as the outcome. It's the earliest point where the result is actually decided, and short enough for a manager to coach against week to week.

**Test each attribute against that outcome.** Photo, bio, focus areas, and open availability all mattered, but differently. Bio showed the cleanest gradient, where every step up paid off. Focus areas mattered least. Availability had the single biggest jump in the data, between a couple of slots a week and a few more, and thin samples at the top, so I capped its credit.

**Separate table stakes from score inputs.** Some things are pass/fail. A patient can't book an empty calendar, an invisible face, or a bio with nothing for search to match.

## What I recommended

- **A "Setup Complete" gate:** has a photo, has a bio, and at least one open slot a week. It becomes a new funnel stage between go-live and first booking. Most providers who failed the gate were missing exactly one item, which makes it very coachable.
- **A Readiness Score for providers past the gate**, weighted by how strongly each attribute tracked with booking, rounded so a rep can compute it by hand: availability 35, bio 30, photo 20, focus areas 15. Booking rates rose with the score in every band.
- **A quality bar set where about half the team already clears it.** The data didn't point to one "correct" threshold, so I picked one that works as a coaching target rather than one most reps would fail.
- **Comp changes, all at once with the scorecard:** move the quota unit from go-live to Setup Complete and lower quotas by the same proportion so nobody looks worse for the same work; a 0.90x to 1.10x quality multiplier that's roughly cost-neutral at launch; 85% of credit at Setup Complete and the remaining 15% once the provider is still booking at day 90; and a job scorecard with the same weights as comp (volume 40, quality 25, outcome 25, speed 10).
- **Behavior change, not just a metric.** Reps treat the sale as done at Setup Complete. Availability becomes a scripted part of the go-live call. Reps draft the bio live on the call instead of assigning it as homework. Coaching targets the single weakest component.
- **Rollout:** a silent background quarter to instrument and validate, review with sales leadership before anything is final, then a pilot against a matched control on actual bookings before pay is affected.
- **Tooling:** for reps, an at-risk queue ranked by how easy each fix is, with drafted outreach per missing item. For managers, an auto-generated 1:1 prep pack. For leadership, the same four numbers every week.

## How I'd measure it

- Setup Complete rate and quality rate against targets, by segment and manager, week over week
- Quota attainment against the reset quota, and actual multiplier cost vs. the cost-neutral model
- Pilot vs. control on 30-day booking rate before any pay impact
- Tool adopters vs. non-adopters on the same funnel metrics. If usage doesn't outperform, the tooling is the wrong fix.
