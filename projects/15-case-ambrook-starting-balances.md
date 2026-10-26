# Case study: getting farm starting balances right (Ambrook, Product Operations)

**Sep – Oct 2026 · Take-home case, two rounds**

Ambrook makes accounting software for farms. The case asked why balance sheet setup is hard for new customers, where an AI agent helps (and where rules, product changes or process work better), how to tell it's working, and what to prototype first. This page describes my approach. The case materials and data belong to Ambrook and aren't reproduced here.

## The goal I set

New customers confirm correct starting balances inside the 30-day trial, with less team time, so fewer of them write in months later with "my balance is wrong". The outcomes behind it are trial-to-paid conversion and 90-day retention.

I proposed three measures to move: days from signup to confirmed balances, balance tickets per new customer in the first 90 days, and team minutes per onboarding. The guardrail was that **no wrong balance reaches a customer's books**, because every report after that builds on it.

## What I found

- **Two accounting rules cause most of the confusion.**
  - A loan payment is part principal (balance sheet) and part interest (expense). Book a $5,000 payment as all expense, and profit looks too low every month while the loan never goes down.
  - A loan taken after the books start begins at $0. Enter a March loan as a starting balance *and* tag its deposit, and the customer owes it twice.
- **The numbers are scattered.** They sit in loan statements, depreciation schedules and bank histories, each with a different date. Several of the sample documents didn't add up, and one "depreciation schedule" was actually a tax valuation.
- **The help exists but arrives at the wrong time.** The rules were documented, but not in front of the customer at the moment they typed a number.
- **The support data needed re-tagging first.** I re-classified the support conversations by topic with a small Python classifier, so the volume could be tied to specific setup problems and to how often each needed a person.

## What I proposed

A pipeline that starts from the customer's documents, before anything reaches the books:

1. The customer sends documents, through the product or by email, starting with full-service customers.
2. **AI** says what each document is, pulls out the numbers, and matches them to the import fields, keeping the page each number came from.
3. **Rules** validate every field and do the math. Every loan needs a lender, a balance and a date. A report's rows must add up to its totals. The start-date balance is computed, not guessed.
4. **The team** reviews each customer as a record in the CRM. Pipeline stages (data received, in review, awaiting corrections, vetted, imported) send the customer emails automatically.
5. **The customer confirms** before anything is imported.

Reviewers' corrections feed back into the agent. Before launch, it would be checked against 20 to 30 past onboardings, comparing its output with what the team had entered.

## What I built

- **A memo** answering each case question through the pipeline: about 2,500 words in round one, under 1,000 in round two after the team asked for a simpler version.
- **A rep review prototype**: a pipeline board with sample farms at each stage, editable amounts, the stage emails, and a document viewer beside the extracted numbers so a reviewer can check each figure against its source.
- **A product prototype** for the customer-side flow, and a swimlane diagram of who does what: customer, AI and rules, team, product.

## What I'd point out

- **AI reads documents, and rules do the math.** Documents vary too much for fixed rules, but arithmetic and validation shouldn't be left to a model.
- **A person approves what goes into the books.** A wrong opening balance looks right, so it needs a check before import, not detection afterwards.
- **Simplify when asked.** The second round kept the same logic on existing tools (CRM pipeline, email, an import template) and left the in-product version for later.

## Tools

Python (pandas, regex classification), HTML prototypes, Claude for document extraction.
