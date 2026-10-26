# CSM bonus dashboard (contributions)

**Sep – Oct 2026 · Customer Success Managers**

A teammate built and owns this dashboard. It shows each CSM their progress on bonus metrics. These were my contributions.

## What I did

- **Churn rule fix.** Logo churn now excludes accounts that never paid and accounts that resubscribed. That matched the definitions in my churn forecast, so the two tools agreed.
- **Activity minutes.** I added "meaningful connections" as phone and meeting minutes per working day, following the schema another team already used for CSM activity.
- **Deploy pipeline.** I moved the image build to the company's container registry with GitHub Actions, so the app could be redeployed by collaborators without re-creating it or losing its configuration.
- **Repository hygiene.** I coordinated moving the repo from a personal account into the company organisation.

## Decisions worth explaining

- **One definition of churn across tools.** If two dashboards disagree, people stop trusting both.
- **Change the pipeline, not the app record.** Re-creating the app would have dropped credentials only its owner could restore.

## Stack

Next.js, TypeScript, Salesforce SOQL, GitHub Actions, GitHub Container Registry.
