# Roadmap, PRD & Prototype (Module 4)

## Your strategic anchors
- **Persona (M2), who are you solving for?:** Venue decision-makers and the analysts who support them. Their goal is to get one specific number (attendance, per-capita spend, ride downtime) that they can act on or defend, under time pressure. The friction confirmed in reconciliation is that they find numbers but can't tell which is official, so they fall back to a personal spreadsheet, an Excel export, or a colleague. The caveat is that my Decision-maker row (58% certified assets, low requests) contradicts this, so check it against real segment data.
- **Primary success metric (M3), your leading indicator:** Share of sessions that check trust info and then use the asset, currently about 39% (100% minus the 61% post-check loss). Proposed target: 50% or more. Supporting signals are a falling duplicate-request count (from 46 a month) and a falling export or local-copy rate among decision-makers and analysts.
- **Moment of misery (M2), the specific friction blocking the goal:** Moments of misery by persona Priya (UXR-01), the findability barrier

Moment: Before the morning briefing, she needs today's attendance against capacity. She scrolls through dashboards for twenty minutes, closes the portal without an answer, and goes back to her own spreadsheet. Why it hurts: The deadline is fixed, and a six-year user still leaves empty-handed. Related defects: BUG-2042 (High), where search matches only exact report names and venue naming is inconsistent. Marcus (UXR-02), the trust barrier

Moment: He finds three dashboards showing "per-capita spend." Each gives a different number, and nobody can tell him which is official. In his words: "I don't need more dashboards, I need to know which one to trust." Why it hurts: He found the data, but he still can't use it, because he can't defend any of the numbers. Related defects: BUG-2058 (Critical), BUG-2061 (High), BUG-2080 (Medium).
- **Guardrail metric (M3), what must not drop or break:** Search → asset-opened rate must stay at or above 52%, with time to find an asset no worse than 18 min. These protect findability while you change how trust is shown. A second guardrail is Mo. 0→1 retention for existing cohorts, which must not fall below its current level.

## Scan the backlog & set a human baseline
- **My instinctive “quick wins” before touching the AI (2 to 3 feature IDs + why):** C4 · Freshness & Definition Panel

## Audit, override & decide
- **Where did you override the AI? (feature + old vs. new score + why):** C8: AI "Ask Your Data" Chat & C9 : Custom Dashboard Builder
- **Did the AI over-value a Sales/Eng request your M2 interviews don’t support?:** No
- **Did it underweight something your M3 cohort/funnel data strongly supports?:** Yes

## Generate your interactive roadmap
- **My “Now” lane (this sprint), the 2 to 3 quick wins I’ll build first:** •	C1 · Official Metric Badge
•	C4 · Freshness & Definition Panel
- **What I cut, and the “no” I’m protecting the scope from:** C10 · Granular Permission Matrix
C9 · Custom Dashboard Builder (as written)
- **Prototype/roadmap screenshot link (paste into your deliverables):** _(not filled in)_
