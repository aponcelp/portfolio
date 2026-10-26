# CX Agent System prototypes

**Jul 2026 · CSMs, Onboarding and stakeholders**

## Problem

The company was designing an AI agent system for Customer Success and Onboarding, with Slack as its first interface. Specs alone didn't show people what it would do for them day to day.

## What I built

Two front-end prototypes with the same architecture, both on synthetic data:

- **Customer Success view.** Each account carries two scores, churn risk and expansion fit, which place it in a 2×2 quadrant. It has an account list, an account detail page with the evidence behind each score, the agents that would fire for that account (with one-click mocked runs), and a portfolio grid.
- **Onboarding view.** The same pattern for the first 90 days: activation speed and setup completeness place each account in a quadrant ("stalled", "coasting", "emerging", "ready to graduate"). It adds milestone checkpoints, roles for the onboarding and implementation specialists, and a customer-facing success plan.

## How it works

React and TypeScript in strict mode, Tailwind and Recharts, with no backend. Data comes from JSON fixtures that follow the schema the production system would produce. I drove the build from a written spec and design references through Claude Code.

## Decisions worth explaining

- **An alignment tool, not a product.** The goal was to get stakeholders to react to something concrete before engineering time was spent. The README says plainly what the prototype is not.
- **Two scores instead of one.** A single health score hides the difference between "at risk but growing" and "safe but flat". The quadrant makes the playbook choice visible.

## Stack

React 18, Vite, TypeScript, Tailwind CSS, Recharts.

## Talking points

- Prototyping to align people on an AI system before it exists.
- Spec-first development with an AI coding agent.
