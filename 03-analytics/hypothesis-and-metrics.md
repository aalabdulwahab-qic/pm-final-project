# Hypothesis & Success Metrics

> **Module 3 · ★ Deliverable 3.** Repo file `03-analytics/hypothesis-and-metrics.md` — part of your submission.
> Do the lab in the **Module 3 · Exercise Guide** (linked from the Module 3 deck), then click **⬇ Download .md** — it saves as this exact file. Commit it here.
> It feeds the **Problem, Value & Hypothesis** slide of your Module 6 final deck.

## Finalized product hypothesis

> Based on Marcus's moment of misery ("I don't need more dashboards, I need to know which one to trust", after he found three "per-capita spend" dashboards with three different numbers) and the funnel data showing that only 31% of sessions check trust info and 61% of those never use the data, I believe that showing one clearly labelled official version of each key metric (with owner, definition and freshness date) for venue decision-makers and the analysts who support them will result in more people using the platform's number instead of a spreadsheet, export or colleague. I expect this to show up as a 28% relative increase (39% → 50%) in the share of trust-checking sessions that end in use. I will protect the search → asset-opened rate (at or above 52%) and time to find an asset (no worse than 18 minutes), and make a go/no-go decision after 6 weeks or [N] sessions, whichever comes later.


## Success metrics

Metric	Type	Target	Why it matters
North-star: duplicate data requests per month	Outcome (lagging)	Fall from 46 to 28 or fewer, the earlier level	It's the closest behavioural proxy in the data for people leaving the platform for colleagues and spreadsheets. It ties to churn and retention, but you'd need the Mo. 0→1 values to prove that link.
Leading indicator: share of trust-checking sessions that end in use	Initiative signal	39% → 50% or more (+11 points, about 28% relative)	It moves first, within weeks. It tests whether an official, labelled version resolves the "which one do I trust?" problem.
Guardrail: search → asset-opened rate, and time to find an asset	Product signal (protects the existing base)	Asset-opened rate stays at or above 52%. Time to find stays at or below 18 min.	The trust change must not make search worse. These are the findability metrics tied to Priya's pain and BUG-2042.
