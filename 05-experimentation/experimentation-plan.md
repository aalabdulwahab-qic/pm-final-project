# Experimentation Plan (Module 5)

## Get your documents ready
- **From M3, your hypothesis sentence:** If we show an "Official" badge, with a tap-to-reveal "Approved by [owner] on [date]", on certified metrics in search results and on the asset page, then venue decision-makers like Marcus will pick and use the owner-approved version instead of abandoning the trust check, because they can see which of several conflicting numbers is the trusted one at the moment of choice. We'll know it worked when check → use rises from ≈ 39% to ≥ 50% without the search guardrail dropping.
- **From M3, your primary success metric & guardrail metric:** From M3, your primary success metric and guardrail metric

Type	Metric	Baseline → Target
Primary	Share of sessions that check trust info and then use the asset (check → use)	≈ 39% → ≥ 50%
Guardrail	Search → asset-opened rate	≥ 52%. Roll back the flag if it stays below this for 7 consecutive days.
Caveat: 39%, 61% and 31% are Lab 1 placeholders. Validate them against real data before you present them as committed targets.
Check against M3: The PRD also mentions an 18-minute time-to-find guardrail, which is read in production. If your M3 lists it as a second guardrail, add it here.
- **From M4, the feature you scoped in your PRD this is what you're testing:** From M4, the feature you scoped in your PRD (this is what you're testing)

C1 · Official Metric Badge is a visible "Official" badge on each certified metric or dashboard, in search results and on the asset page. A tap-to-reveal note says who approved it and when. This lets Marcus see which of three conflicting "per-capita spend" dashboards is the trusted one (BUG-2058, BUG-2061, BUG-2080).

Prototype: 3 screens (Search Results → Asset Page with approval popover → Confirmation). It uses hardcoded data, useState only, no login and no external APIs.
Launch set: per-capita spend and attendance. Each has exactly one official asset.
Evals to test against:
E1: ≥ 90% of participants pick the official dashboard first.
E2: median time-on-task ≤ 30 seconds.
E3: 0 false badges.

## Define your experiment parameters
- **Feature under test pull from your M4 PRD:** C1 · Official Metric Badge. The treatment arm shows an "Official" badge (shield-check icon + text) on search result cards and the asset page header, for the one certified asset each of per-capita spend and attendance. Tapping, hovering or focusing the badge opens a popover reading "Approved by {owner_name} on {certified_date}". The badge fails closed if is_official, owner or date is missing. The control arm sees today's UI. Non-official assets look the same in both arms.
- **Persona pull your M2 persona:** Marcus (UXR-02), a venue decision-maker who finds three "per-capita spend" dashboards with three different numbers and can't tell which is official (BUG-2058, BUG-2061, BUG-2080). The secondary persona is Priya (UXR-01), an analyst.
- **Expected outcome the behaviour change you expect, from your M3 hypothesis:** Among sessions that check trust info on a certified metric, more users go on to use the asset. They no longer abandon the check or export to Excel, because the official version is marked at the point of choice.
- **Primary success metric the one number that defines success, from M3:** Check → use rate: the share of sessions that check trust info and then use the asset. "Use" is defined as the asset_used_after_trust_check event, and the exact definition of "use" is still an open item.
- **Baseline rate today's rate of your primary metric, from your M3 data:** ≈ 39% (the other ≈ 61% check and then don't use). This is a Lab 1 placeholder, so validate it before you calculate the final sample size.
- **Guardrail metric & boundary what must not break, and how far it can move before you investigate:** Search → asset-opened rate, which must stay ≥ 52%. Investigate if the treatment arm falls more than 2 pp below control, or if it falls below 52% for 7 consecutive days, which triggers the flag rollback. This is a different number from the primary metric. It checks that the badge doesn't make people give up on search. Also monitor the 18-minute time-to-find as a secondary read.
- **Minimum Detectable Effect (MDE) the smallest improvement worth shipping, your floor:** 5 percentage points (39% → 44%). This is the floor worth shipping. The PRD target of ≥ 50% is the goal, not the floor, and a real lift of 5–10 pp would still justify shipping.
- **Sample size per arm use the calculator in the builder, baseline + MDE:** ≈ 1,520 per arm (≈ 3,040 total) at 80% power and 5% significance, with a baseline of 39% and an MDE of 5 pp. Enter 39 and 5 in the builder. Calculators differ slightly, so expect roughly 1,520–1,525. Using the PRD target as the MDE (11 pp, 39% → 50%) would need only ≈ 320 per arm, but it would miss real lifts between 5 and 10 pp.
- **Traffic split & test duration 50/50 standard · cover ≥ 2 weekly cycles:** 50/50 split, randomized by user so one person doesn't see both variants. Run at least 14 days to cover two full weekly cycles, because venue traffic probably swings around event days. Then keep running until both arms reach ≈ 1,520. The duration formula is 2 × 1,520 ÷ daily eligible users. The denominator is only users who check trust info, not total traffic, so get that number from analytics. Fix the end date in advance and don't stop early.
- **Significance threshold p < 0.05 is standard, explain any deviation:** p < 0.05, two-sided, with no deviation, for the primary metric. Evaluate the guardrail as a "no meaningful drop" check against the 2 pp boundary, not as a second win test. This keeps one success metric and one safety metric.

## Define your control and variant
- **Control (A) the current experience, reference your M2 moment of misery and M3 funnel/workflow data:** Marcus searches "per-capita spend" and gets three dashboards (Finance Analytics, Venue Ops, and a copy) with three different numbers. Nothing in the list or on the asset pages shows which one is the owner-approved version (BUG-2058, BUG-2061, BUG-2080). He opens several, checks whatever trust information exists, and in about 61% of those sessions he doesn't use the asset. He asks a colleague or exports to Excel instead. Only about 39% go on to use it.

Search results: three cards with title, asset type, owning team, description and an "Open" action. No badge and no certification label.
Asset page: title, headline number and chart. No badge and no approval popover.
Certification data: the records may exist in the backend, but nothing is rendered.
Ranking: search order is unchanged.
- **Variant (B) your single change, copy the relevant screens & functional requirements from your M4 PRD:** Add the Official badge and its approval popover to certified assets. Everything below is copied from the PRD.

Search result cards (Screen 1): an "Official" badge (shield-check icon plus text) at the top-right of exactly one card. For the per-capita spend search, that is Per-Capita Spend, Finance Analytics. The other two cards have no badge and no "not certified" label.
Asset page header (Screen 2): the same badge, focusable, with text contrast of at least 4.5:1. Tapping, hovering or focusing it opens a popover reading "Approved by {owner_name} on {certified_date}" (FR2–FR4). The popover is template text only. Esc or an outside click closes it and returns focus to the badge.
Scope: the two launch metrics, per-capita spend and attendance, each with exactly one official asset (FR5).
Fail closed (FR7, Behaviors 4–5): no badge if is_official, owner or date is missing. No badge on either asset if two are flagged official for the same metric.
Performance (FR8): no extra network call, and list render time rises by no more than 100 ms at p95.
The badge and popover count as one change because the popover is the badge's own provenance note. It isn't a separate feature.

Amendments to the PRD for the live test
These come from the PRD's prototype stand-ins, which would break the test if copied into production.

Leave out the "Use this number" button and Screen 3. They exist only to simulate the "use" event in the prototype. In production, "use" is measured by the real asset_used_after_trust_check event (the exact definition of "use" is still open).
Fire asset_used_after_trust_check in both arms. Behavior 10 says "flag off → no events fire", which would leave you with no control data. Change it to: the flag controls only the badge UI and badge_viewed. The check → use event logs for everyone, with the arm recorded.
- **Isolation check, what has NOT changed? list everything identical between arms (app version, recommendation engine, notifications, onboarding). If something changed inadvertently, your test is compromised.:** Held identical in both arms	Detail
App version and release	Same build, with the badge behind a flag. Only the flag differs.
Search behavior	Same ranking, with no official-first sorting (S1), no "Official only" filter (S3) and no search-intent features (C3, C8).
Non-official assets	Same cards and pages, with no "Not certified" label (S2).
Asset content	Same numbers, charts, owning teams and descriptions.
Trust information that exists today	Identical in both arms.
Permissions and access	No changes (C10 is cut).
Exports	No provenance stamp (C6).
Notifications and onboarding	No announcements, tooltips or tours about the badge.
Certification set	The same two metrics are certified in the data for both arms. Control just doesn't render the badge.
Instrumentation	The same check → use and search → asset-opened events in both arms.
Assignment	Randomized by user, 50/50, with the same eligible population.

## Formalize your hypothesis & shipping criteria
- **Your hypothesis (filled in):** I believe that adding an "Official" badge, with a tap-to-reveal "Approved by {owner_name} on {certified_date}" popover, to the certified per-capita spend and attendance assets in search results and on the asset page for Marcus (UXR-02), a venue decision-maker who finds three conflicting "per-capita spend" dashboards and can't tell which is official, will result in more trust-checking sessions ending in use of the asset, instead of abandonment or an export to Excel, as measured by a ≥ 5 percentage point increase (39% → ≥ 44%, about a 13% relative lift) in check → use rate (asset_used_after_trust_check ÷ sessions that check trust info) within 14 days, extended until both arms reach about 1,520 users. We will protect search → asset-opened rate throughout the test.
- **Your shipping criteria (filled in):** SHIP if check → use improves by ≥ 5 pp (39% → ≥ 44%) at p < 0.05, two-sided, and search → asset-opened stays ≥ 52% and does not fall more than 2 pp below control, at the end of the 14-day test (extended until about 1,520 users per arm).

ITERATE if the direction is positive but the lift is below 5 pp. This includes a significant lift smaller than the MDE and a positive but non-significant result. Next, check whether the badge is being seen (badge_viewed) and tapped, whether the popover is being opened, and whether only some segments move.

KILL if check → use shows no improvement or moves negatively.

HOLD if the primary metric hits the ship bar but the guardrail is breached. Do not ship. Investigate the search drop first, then re-test. The template has no rule for this case, so I added it.

The read date is fixed at the end of the test window, which is 14 days or the date both arms reach about 1,520, whichever is later. I recommend writing that calendar date down before launch. No results are reviewed before then, except the safety checks below.

Pre-committed safety exceptions (these don't count as peeking at results):

Rollback: if search → asset-opened is below 52% for 7 consecutive days, the flag goes off.
False badge: if any badge appears on a non-official asset or on a record with a missing owner or date, stop the test. This is the E3 zero-tolerance rule.
Validity conditions. If any of these happen, the result is void and you rerun:

C4 goes live for either arm.
The official asset or its owner changes mid-test.
A sample ratio mismatch appears, meaning the arms are not close to 50/50.
- **Hardest parameter to define, and did it change your hypothesis? quick debrief:** The hardest parameter was the MDE, tied to the definition of "use". The PRD target of ≥ 50% is an aspiration. The floor worth shipping is smaller. Setting the MDE at 5 pp instead of 11 pp raised the sample from about 320 to about 1,520 per arm, so that choice decided how long the test runs. The primary metric's definition of "use" was also still open. The prototype used a "Use this number" button as a stand-in, and that can't be measured in production.

Yes, it changed the hypothesis in three ways:

It moved the success claim from "reach 50%" to "improve by at least 5 pp". 50% stays as the goal.
It forced me to write "use" as a logged event that fires in both arms. The PRD's rule that no events fire when the flag is off would have left no control data.
Isolating the variant showed that C4 must stay off during the test, or the result can't be attributed to the badge.
