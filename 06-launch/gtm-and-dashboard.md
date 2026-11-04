# GTM Strategy & Success Dashboard (Module 6)

## Get your prior work ready
- **The feature you're launching from your M4 PRD, one feature, not a list:** C1 · Official Metric Badge is a visible "Official" badge (shield-check icon plus text) on certified metrics and dashboards, in search results and on the asset page. Tapping, hovering or focusing it opens a popover reading "Approved by {owner_name} on {certified_date}".

Why it exists: Marcus finds three conflicting "per-capita spend" dashboards and can't tell which one is trusted (BUG-2058, BUG-2061, BUG-2080).
Launch scope: per-capita spend and attendance, each with exactly one official asset.
Fail closed: no badge if is_official, owner or date is missing, or if two assets are flagged official for the same metric.
Not in this launch: C4 (Freshness & Definition Panel), official-first sorting, an "Official only" filter, "Not certified" labels, and export stamps
- **What your M5 experiment told you shipped / iterating, the evidence behind the launch:** What your M5 experiment told you

Item	Your answer
Test	50/50 randomized A/B test, badge versus today's UI. It runs at least 14 days, with about 1,520 users per arm.
Primary metric	Check → use rate: 39% baseline, with a ship bar of ≥ 5 pp (≥ 44%) at p < 0.05. The goal is 50%.
Guardrail	Search → asset-opened stays ≥ 52% and no more than 2 pp below control.
Decision rule	Ship, Iterate (positive lift below the MDE), Kill (no lift or negative), or Hold (the primary metric hits the bar but the guardrail breaks).
- **Your persona pull your M2 persona, this anchors your audience:** Primary: Marcus (UXR-02). A venue decision-maker who relies on per-capita spend and attendance numbers. He finds several dashboards with conflicting figures. In about 61% of his trust-check sessions he doesn't use the asset. He asks a colleague or exports to Excel instead.
Secondary: Priya (UXR-01). An analyst who builds and maintains these assets. She is also a likely owner or approver.

## Set your goal, then your audience
- **Primary GTM goal awareness · engagement · conversion, pick one:** Engagement. Get existing users to use the official version of a certified metric, instead of abandoning the trust check or exporting to Excel.
- **Why this goal? what makes this the right goal for this feature right now:** The feature lives inside the existing product. The badge appears in search results and on asset pages that users already visit. Nobody needs to find out the product exists, so awareness is the wrong goal.
The problem is a drop-off, not a missing audience. About 61% of Marcus's trust-check sessions end without use. He asks a colleague or exports to Excel instead (BUG-2058, BUG-2061, BUG-2080). That is an engagement gap in a flow people already use.
Why not conversion? There is no sign-up, purchase or upgrade. The "conversion" here is check → use, which is the same number the M5 test measures. Engagement keeps the GTM goal tied to that metric. If your course defines conversion as moving a user from one funnel step to the next, you could justify that label. The audience and metric below stay the same either way.
Why now? The Week 0 certification is the trigger. The badge only has value once someone has named the owners and approved the two launch metrics. The launch is therefore about adoption of the certified assets, not about announcing a feature.
Goal statement: Raise check → use on certified assets from about 39% to at least 44% (stretch goal 50%) among users who look for per-capita spend and attendance.
- **Target audience the specific segment your goal implies, be precise:** Primary: Marcus-type users (UXR-02). These are existing venue decision-makers who:

search for or open the per-capita spend or attendance assets,
and have checked trust information on one of them (the same population the M5 test measured).
To make it precise, define the segment as a query, such as "users with at least 1 search or asset open on these two metrics in the last 90 days". Then fill in the size from analytics: ___ users.

Secondary (enablement audience, not the engagement target): Priya-type owners and approvers (UXR-01). These are the named owners of per-capita spend and attendance. The badge shows "Approved by {owner_name}", so they need to know their name will appear and what approving means. They are a small, named group, and the launch depends on them.

## Size your launch
- **Launch tier S (minimal) · M (targeted) · L (multi-channel) · XL (full GTM):** S (minimal), with a small targeted enablement step for the two owners.
- **Justification reach + revenue impact + what silence would risk:** Reach is narrow.

Only two metrics, per-capita spend and attendance, get a badge.
Only users who touch those assets can see it, so it reaches one segment of existing users (Marcus-type), about ___ users (from Step 1).
There are no new markets, no external audience, and no new surface. The badge sits inside search results and asset pages people already use.
Revenue impact is indirect.

There is no sign-up, price change or upgrade.
The value is internal: fewer Excel exports and colleague pings, and decisions made on the right number.
If you can estimate it, size it as ___ hours saved per month. Don't invent a revenue number.
Silence carries little risk.

The badge communicates itself. It appears at the moment of choice, so users don't need an announcement to benefit.
If nobody is told, users still see "Official" where they already look. That is low risk compared with a feature that is hidden or needs learning.
The real risks are about quality and owners, not messaging.

Owners. The two owners must know their name will appear and what approving means. If they don't, the popover shows "Approved by" a person who didn't expect it. This is the one place silence costs you.
False or missing badge. A wrong badge damages trust more than no badge. That is a QA and fail-closed problem (E3), not a comms problem.
Over-investing. A multi-channel campaign for a two-metric badge would cost more than the problem is worth and would add noise to the product.
- **Is this a launch or a release? does it need go-to-market, or can it just ship?:** It's a release with a small launch layer.

Part	Treatment
Badge for Marcus-type users	Release. Ship behind the flag, with no announcement, tooltip or tour.
Two named owners	Launch. A short, direct heads-up: what the badge means, what their approval implies, and who to contact if the badge is wrong.
A brief in-product or team note	Optional. One line after rollout, such as "Certified metrics now show an Official badge".
This also keeps the isolation rule from the test. The M5 control and variant arms had no announcements. Introducing a campaign at launch would change the conditions the lift was measured under.

## Choose your top three channels and plan assets
- **Channel 1 owned / earned / paid, and why it reaches your audience:** Owned: the in-product badge itself (search cards and asset page)
Why it reaches the audience: It sits at the moment of choice, in the search results and asset pages Marcus already uses. It needs no announcement or tour.
What it replaces: A campaign. Making the badge itself the message also keeps the rollout the same as what the M5 variant arms saw.
Track: badge_viewed, popover opens, and check → use.
- **Channel 2 owned / earned / paid, and why:** Owned: a direct note to the two named owners (email or Slack DM)
Why it reaches the audience: The owners are a small named group. A direct message works better than a broadcast.
Content (about 5 lines):
The badge goes live on date X for per-capita spend and attendance.
It shows "Approved by {your name} on {date}".
Approving means you stand behind this as the official version.
How to withdraw or change approval.
Who to contact if the badge looks wrong.
Timing: Send it before the flag turns on. If owners learn about it from the popover, it's too late.
- **Channel 3 owned / earned / paid, and why:** Earned: owner and team word of mouth, plus one line in the existing release notes
Why it reaches the audience: Marcus already asks colleagues which dashboard to trust. If the owners and the colleagues he asks say "use the Official one," the badge gets reinforced through the channel he already relies on.
Release note (optional): One line in your normal changelog or team channel: "Certified metrics now show an Official badge. Hover or tap it to see who approved it and when."
Timing: Post it after the A/B test is read and the rollout starts, so it doesn't contaminate the test.
Honest limit: Earned reach here is small and hard to measure. Treat it as support, not as a primary driver.
- **Enablement & assets what Sales / CS / Support need, plus the assets to build (one-pager, demo, etc.):** Sales doesn't apply, because this is an internal feature. The audiences are Support, the data team that answers "which dashboard?" questions, and the two owners.

One shared message for everyone:

Official = approved by the named owner on the date shown.

Don't say "accurate", "verified correct" or "guaranteed". The badge shows approval, not a data-quality check. If Support promises more than that, a wrong number under a badge will damage trust.

Asset	For	Contents	Effort
Owner one-pager	The 2 owners	What approval means, how to withdraw it, and a contact	Small
Support FAQ / macro	Support, data team	4 answers: What does Official mean? Why doesn't my dashboard have a badge? Why do I see no badge on a metric that should have one? How do I report a wrong badge?	Small
30-second demo (GIF or screenshot)	Anyone asked "what's this?"	Search → badge → popover	Small
Wrong-badge runbook	Eng, on-call	Turn the flag off, check is_official, owner and date, and the two-assets-flagged case. Tie it to the E3 zero-false-badge rule.	Small
Release-note line	All users	One sentence (see above)	Tiny
Launch slide	Final project	Goal, tier S, channels, owner dependency, metrics	Small

## Make it executable
- **Ownership named owner per key activity, individual, not department:** Activity	Role needed
Overall launch and go/no-go call (reads the M5 result, decides the rollout)	Product manager (you)	
Name the certified owners for per-capita spend and attendance (the Week 0 decision)	Data governance lead, or whoever can assign ownership	
Approve each metric (their name appears in the popover)	Owner of per-capita spend	
Owner of attendance	
Build and flag the badge, including fail-closed behavior	Engineering lead	
Event definitions and the A/B read: asset_used_after_trust_check, badge_viewed, the guardrail, sample-ratio check	Analyst or data scientist	
Owner one-pager and 5-line owner note	Product manager (you)	
Support FAQ and macros, and the "wrong badge" report inbox	Support lead	
Wrong-badge runbook and the flag kill switch	On-call engineer	
30-second demo (GIF or screenshot)	Designer, or you	
Release-note line	Product manager (you)	
Post-launch metrics review	Analyst
- **Budget & resource gaps what costs extra, and any asset you can't currently build:** Direct spend: likely $0. There is no paid channel, no campaign and no new vendor, as chosen in Step 3.

What costs extra (time, not cash):

Item	Estimate (assumption)	Why it matters
Engineering: badge, popover, flag, fail-closed logic	Already in the C1 scope, so no new cost	Don't count it twice.
Engineering: instrumentation changes from the Step 2 amendments (fire the event in both arms, drop the prototype button)	~1–2 days	Without it the A/B has no control data.
Analyst: define "use", build the read and the sample-ratio check	~2–3 days	The test can't be read without it.
Owners' time: read the note, confirm approval	~30 min each	Small, but the launch can't start without it.
Support: FAQ, macros, inbox	~0.5 day	Low, but it must happen before the flag goes to 100%.
Runbook and on-call coverage during rollout	~0.5 day, plus on-call attention for week 1	This is the main risk control for false badges (E3).
What you can't build or don't have yet (gaps):

Named owners. This is the hard blocker. The badge shows nothing without them.
A final definition of "use". The success metric and the dashboards depend on it.
Segment size and the eligible daily traffic. You need them to date the test and report reach.
An M5 result. The plan can't leave "conditional" without it.
A real "wrong badge" escalation path. Someone must be able to turn the flag off outside working hours, or you must accept that gap and say so.
Any time-saved or revenue figure. Don't invent one. Show it as unknown.
If a gap can't be closed: cut scope rather than add cost. For example, launch with one metric instead of two, or ship the badge to the 50% test arm only.
- **Timeline Phase 1 beta → Phase 2 launch moment → Phase 3 post-launch:** Phase 0 · Gates (before anything is exposed)
Complete these first. Nothing launches until all four are done.

 Both launch metrics have a named owner who has approved (Week 0 decision).
 "Use" event defined and logging in both arms.
 C4 confirmed off for both arms.
 Owner note sent, and the Support FAQ and runbook ready.
Phase 1 · Beta (the M5 experiment)
≈ T-3 weeks to T-1 week. The A/B test is your beta.

50/50 split, at least 14 days, until about 1,520 users per arm.
No announcements, tooltips or release notes. They would change the conditions you're measuring.
Only the safety exceptions are checked early: the 7-day guardrail rollback and any false badge.
Gate at the read date: apply the pre-committed rule.
M5 result	What happens
Ship	Go to Phase 2 with the tested variant unchanged.
Iterate	Hold the launch. Check badge_viewed and popover opens, then re-test.
Hold (guardrail breached)	Don't launch. Fix the search drop first.
Kill	Nothing to launch.
Phase 2 · Launch moment (T)
Small on purpose, matching tier S.

T-2 days: Confirm the owners still approve and that the "official" asset hasn't changed.
T: The flag goes to 100%. A staged ramp (for example 50% → 100% over 1–2 days) is optional and cheap.
T to T+1 day: Post the release-note line and share the demo GIF. This is deliberately after the test read.
On-call is active and the Support FAQ is live.
Phase 3 · Post-launch
T+1 week: Check for false badges (target is zero) and for search → asset-opened staying at or above the guardrail. Review support tickets about the badge.
T+2 weeks: Compare check → use against the 39% baseline and the ≥ 44% bar. Because the flag is at 100%, there is no control arm, so compare with the pre-launch period and the M5 result, and note that this read is weaker than the test.
T+4 weeks: Make the expansion decision: add more certified metrics, or sequence C4. Go back to tier M only if the segment is larger than expected or the result suggests the badge needs more explanation.
Ongoing: Re-confirm each owner's approval on a schedule, so a stale "Approved on" date doesn't undermine the badge. This is a gap in the PRD, so decide who owns it.

## Define how you'll know it worked
- **Success metrics 2 to 3 metrics that match your GTM goal:** The goal is engagement: get existing users to use the official version. The metrics measure that behavior and not reach or sign-ups.

#	Metric	Definition	Target
1. Primary	Check → use rate	Sessions with asset_used_after_trust_check ÷ sessions that check trust info, on the two launch metrics	≥ 44% (about 39% + 5 pp), stretch 50%
2. Behavior	Official-asset share	Of sessions that open or use a per-capita spend or attendance asset, the share that land on the official one	Rising versus the pre-launch share. Set a number once you have the baseline: ___%.
3. Health / guardrail	Search → asset-opened rate	Searches that lead to an asset being opened	≥ 52%, and no more than 2 pp below the pre-launch level
Hard safety check (not a success metric): false badges must be 0. A badge on a non-official asset, or on a record with a missing owner or date, triggers the flag kill switch (E3). Don't average it into a rate.

Diagnostics (read them, don't target them):

badge_viewed rate, to show whether users see the badge at all.
Popover open rate.
Excel-export rate on the two metrics, if you can measure it. It's the closest proxy for "the user didn't trust it", but it needs instrumentation.
Support tickets about the badge.
Why these three:

Metric 1 is the same number the M5 test measured, so the launch stays tied to the evidence.
Metric 2 shows the badge changed which asset people choose. Metric 1 alone could move for other reasons.
Metric 3 protects against the badge slowing down search.
Popover opens are a diagnostic because they are ambiguous. A high rate can mean curiosity or doubt.
- **Bad signal to watch for e.g. high reach, zero signups = message-market mismatch:** Signal	What it likely means	What to do next
badge_viewed is high, but check → use is flat	Users see it but don't trust or understand "Official". The message-market mismatch is on the badge's meaning.	Check popover opens. Rewrite the popover text. Check that owners are credible to Marcus.
badge_viewed is low, and check → use is flat	The badge isn't being seen, or fail-closed is hiding it because owner or date data is missing.	Check the render rate against the number of certified assets. Fix the data gaps first.
Official-asset share is up, but check → use is flat	People pick the right dashboard but still don't use it. The problem is something else, such as freshness or definitions.	Bring the sequencing of C4 forward.
Check → use is up, but search → asset-opened is falling	The badge is making people hesitate or abandon search.	Treat it as a Hold. Investigate the search drop before expanding.
Popover opens are very high, and use is low	Users need to verify the badge before trusting it, so it isn't self-explanatory.	Put more information on the card. Improve the owner one-pager.
Lift after launch is much smaller than in M5	The test effect was novelty, a selection effect, or a change in the certification set.	Check whether owners or the official asset changed. Don't expand yet.
Any false badge, or a "wrong badge" ticket	The fail-closed logic or certification data failed.	Turn the flag off, run the runbook, and find the cause before turning it back on.
Approval dates going stale (for example, months old)	The badge looks neglected and undermines trust.	Set up a re-approval schedule. This is the unowned PRD gap from Step 4.
- **Most likely post-launch decision double-down · iterate · pivot · deprioritize, and what would trigger it:** Double-down, carefully. If M5 reads Ship, the badge is a low-cost, in-product change with a defined audience, so expanding it is the natural next step.

Decision	Trigger (at T+4 weeks)	Action
Double-down	Check → use ≥ 44% and holding. Guardrail intact. Zero false badges. Official-asset share is up.	Add more certified metrics, in the same fail-closed way. Then decide whether to sequence C4. Move to tier M only if the audience grows past what S can cover.
Iterate	Lift is positive but below 5 pp, or badge_viewed is high with flat use.	Fix the badge's meaning or visibility (popover text, placement, owner credibility). Re-test if you can.
Pivot	Official-asset share is up but check → use is flat. Users choose correctly but still don't use it.	Treat trust as a freshness and definition problem. Move the effort to C4, and keep the badge as is.
Deprioritize	No lift after an iteration, or the owners can't keep the approvals current.	Stop expanding and leave it on only for the two metrics, or turn it off.
Rollback is separate from these decisions. Search → asset-opened below 52% for 7 consecutive days, or any false badge, turns the flag off right away, as pre-committed in M5.

Honest limit: with the flag at 100% there is no control group. Compare with the pre-launch period and the M5 result, and say that this read is weaker than a test. For a stronger read, keep a small holdout (for example, 5–10% of users with no badge) for the first month if you can accept it.
