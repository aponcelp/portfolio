# Case study: reading 12 months of customer revenue before a first QBR

**Jul 2026 · Take-home case, customer operations · Excel model plus short written answers, about one hour**

The scenario: a vertical SaaS company serving field-service businesses. Thirty days into a Director of Customer Operations role, the chief customer officer wants your read on the last year of customer revenue before your first QBR. Using a customer-by-month dataset, build the ARR snowball, a retention KPI dashboard by segment, and a six-month forecast, then answer questions on trends, priorities, risk, and where to invest. The company, its data and the prompt text aren't reproduced here.

## My approach

I built the model bottom-up from the raw movements, all formula-driven: an ARR snowball by month (opening, new logo, upsell, cross-sell, downsell, churn, closing), then monthly net revenue retention (NRR), gross revenue retention (GRR), churn rate, and expansion rate, in total and by segment (Enterprise, Mid-Market, SMB).

The point of the dashboard was to show the GRR and NRR side by side, because they were telling different stories. NRR said the company was growing. GRR said it was losing a meaningful share of its base before any expansion was counted. The gap came almost entirely from one segment's expansion covering for the other two segments' losses.

For the forecast, I set every assumption as a rate on opening ARR by segment, wrote down the basis for each one, and adjusted the historical averages where the trend argued for it: trimmed expansion where it was slowing, raised churn where it was speeding up, and set new-logo ARR below the average because one outlier month inflated it.

## What I recommended

- **Lead with the two trends that matter.** Enterprise was carrying the company: strong net retention, real expansion, no churn, and most of the book. Mid-Market and SMB were losing revenue, and Mid-Market churn was speeding up.
- **For the next 90 days, prioritize stopping churn over chasing expansion.** Run churn-reason analysis on SMB and Mid-Market accounts and start tracking a save rate. Then point retention resources at Enterprise, where the growth engine is.
- **Watch the Enterprise account that had already downsized.** One downsell at the top of the book is the earliest signal you get. Go deep on that account in the first 30 days, and check whether what happened there could happen to other Enterprise customers.
- **Shift investment by segment.** Increase it in Enterprise with a high-touch CSM motion. Pull back on SMB: move it to a low-cost or product-led motion, redeploy that capacity to Enterprise and at-risk Mid-Market, and shift new sales toward Mid-Market and Enterprise.
- **Be explicit about where the forecast could be wrong.** It rests on two assumptions: Enterprise keeps expanding at roughly its recent monthly rate, and Mid-Market and SMB keep churning at current rates because nothing is yet in place to change that. The fragile one is Enterprise expansion. Most of it landed in one quarter and it was already slowing. If that quarter was an outlier, the book goes flat or down instead of growing, because Enterprise drives almost everything.

## How I'd measure it

- GRR alongside NRR every month, total and by segment, so expansion can't hide churn
- Churn rate and downsell rate in Mid-Market and SMB, plus save rate on at-risk accounts once churn reasons are tagged
- Enterprise expansion rate against the forecast assumption, as the early warning for the scenario where the forecast breaks
- Forecast vs. actual closing ARR each month, with assumptions updated in writing when they drift
