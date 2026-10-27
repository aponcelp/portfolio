# Case study: rolling out territory-based lead routing

**Sep 2026 · Take-home case, revenue operations · 13-slide proposal plus a systems design appendix**

A fast-growing healthcare marketplace wanted to move its provider sales team from a national round robin to location-based territories, because what a rep sells differs by state and leads were reaching reps in the wrong timezone. I was asked to act as both project lead for the change and owner of the technical design, with a cross-functional plan, documentation approach, and timeline. The company, its data and the prompt text aren't reproduced here.

## My approach

I started from what actually changes for a lead. Only one step is new: the lead gets stamped with a territory from the provider's state, then round-robins inside that territory instead of nationally. Everything else in the plan follows from making that one step reliable and fair.

Then I looked for what the model leaves open. Two gaps came straight out of the brief's numbers:

- **Referrals sit outside the model.** Referred leads go to the referring rep regardless of state, so territory routing only governs part of the volume. Any report on lead distribution has to say which pool it measures.
- **Equal volume isn't equal coverage.** Territories were drawn for equal lead volume, but some reps would have to know far more states than others on the same quota.

For the design, I wrote requirements before tools: moving a state is a record edit, not a release; eligibility follows certification; no lead goes unassigned; every routing decision is logged so a rep can see why they got a lead.

## What I recommended

- **Get the state from the provider's license number, not a form field or IP lookup.** Providers who bill insurance already have a national ID; one lookup in the public registry returns practice address, specialty, and practice type. Shorter form, better data.
- **Count-based round robin inside the pool of certified reps,** with a half share while a rep is still certifying and skips for anyone unavailable. Count-based because the promise is equal opportunity, and a count is what a rep can check for themselves. No backfill after PTO, written down in week 1 so it isn't argued in week 3.
- **Referrals:** keep the current rule if fewer than roughly 15% of referrals cross a territory line. Otherwise route out-of-territory referrals to the territory and pay the originator a fixed bonus on acceptance, so their payout doesn't depend on someone else closing.
- **Protect earnings for one quarter.** A rep's pay moves in week 1; the conversion benefit shows up a quarter later. Make up any shortfall, brief managers before reps, and show every rep their own numbers.
- **Phase the rollout around certification capacity,** with a matched control group of reps staying on the old model through Phase 1 so any conversion change can be attributed to routing, not seasonality.
- **Audit reports before go-live.** Territories don't break dashboards, they make them mislead: a rep leaderboard quietly starts comparing people in different markets.
- **AI with guardrails:** a pre-call brief that cites only the approved rate sheet, and follow-up drafts the rep reviews and sends.

## How I'd measure it

Agreed with all teams in week 1, measured against the control group or a 12-month baseline:

- Time from lead to first contact: under 5 minutes and faster than control (daily for the first month)
- Conversion on non-referral leads: above control by a margin agreed up front (weekly)
- Lead spread within a territory: under 5% variation between reps (weekly)
- Leads that couldn't be routed: under 2% of daily inbound (daily; usually the first number to move)
- Certification coverage per rep, a better ramp measure than days elapsed (weekly)
- Time to a new hire's first win vs. reps hired before the change (monthly)
- Rep sentiment and attrition vs. a pre-launch pulse (weeks 1, 4, 12)
