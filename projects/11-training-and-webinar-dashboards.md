# Training Hub, webinar and campaign-link tools

**Jun – Jul 2026 · Customer education and CX leadership**

Three small tools around customer education: was the training content used, did webinars help, and could anyone attribute the traffic?

## Training Hub growth dashboard

Weekly momentum, trends, retention and content performance for the customer training site, from product analytics.

- **The proxy is not an open query console.** The browser can only ask for queries **by name**, such as `weekly` or `retention`. The query definitions live on the server, and any unknown name is rejected. A leaked URL can't run arbitrary queries.
- The API key never reaches the browser or git. There's an optional password gate for anything shared by URL.
- It's a static page plus one server file, with no build step.

**Stack:** Express, Chart.js, PostHog query API.

## Webinar dashboard

Did webinars reduce tickets and churn? This starts with the funnel: registered, then attended, then engaged, then stayed to the end.

- Pick a webinar from a light list first, then load its full stats on demand, so every API call stays small and the page never hangs on a large workspace.
- Every funnel stage has a written definition, and the "stayed to end" threshold is configurable.
- Zero runtime dependencies: a plain Node HTTP server proxies the API.

**Stack:** Node `http`, vanilla JS, Livestorm REST API.

## UTM link generator

A single-file tool that builds campaign links following the team's tagging convention. You pick from dropdowns, and the tool enforces all five tags, lowercase values, no spaces, and fallbacks instead of empty fields.

**Why it mattered:** attribution only works if everyone tags the same way, and a tool enforces that better than a style guide does.

**Stack:** one HTML file.
