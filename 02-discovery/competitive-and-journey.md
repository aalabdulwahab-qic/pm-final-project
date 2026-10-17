# Competitive Analysis & Journey Map (Module 2)

## Responses
- **Role, who are you solving for? (the specific user segment or profile):** Primary segment: venue decision-makers and the analysts who support them. These are people who need a specific number, such as attendance, per-capita spend, or ride downtime. They have to act on it or defend it, usually under time pressure.
- **Goal, what is this user ultimately trying to achieve?:** Ultimate goal: Get a number they can act on or defend, quickly, without a workaround.

Finding a dashboard isn't what they want. The dashboard is a means to a decision, a briefing, or a presentation.
- **Friction, the main barrier (moment of misery) stopping them from succeeding:** Main barrier: The platform can't take them from a question to one answer they can verify. They can't find the right asset, and when they do find something, they can't tell whether to trust it.

Moments of misery by persona
Priya (UXR-01), the findability barrier

Moment: Before the morning briefing, she needs today's attendance against capacity. She scrolls through dashboards for twenty minutes, closes the portal without an answer, and goes back to her own spreadsheet.
Why it hurts: The deadline is fixed, and a six-year user still leaves empty-handed.
Related defects: BUG-2042 (High), where search matches only exact report names and venue naming is inconsistent.
Marcus (UXR-02), the trust barrier

Moment: He finds three dashboards showing "per-capita spend." Each gives a different number, and nobody can tell him which is official. In his words: "I don't need more dashboards, I need to know which one to trust."
Why it hurts: He found the data, but he still can't use it, because he can't defend any of the numbers.
Related defects: BUG-2058 (Critical), BUG-2061 (High), BUG-2080 (Medium).
- **External tools, the outside platforms or tools the user is forced to use:** Personal spreadsheet, Excel export of a dashboard table, Colleagues as a source of numbers
- **The process, the 3 to 5 manual steps the user takes to get the job done:** Open the portal before the morning briefing. (documented)
Scroll through dashboards for today's attendance against capacity. (documented)
After about 20 minutes, give up and close the portal. (documented)
Open her own spreadsheet and get the number from it. (documented that she returns to it; how it gets its data is unknown)
Take that number into the briefing. (inferred)
- **Core frustration, the exact moment the process feels most “broken”:** Priya: The moment she closes the portal after 20 minutes with nothing. A six-year user with a fixed deadline gets no answer, and the spreadsheet fallback only starts after that time is lost.
Marcus: The moment three different numbers appear and nothing says which is official. He found the data but can't use it.
- **The evidence, a specific quote or behavior from the research that proves this:** Type	Evidence	Source
Behavior	Priya scrolls for twenty minutes, closes the portal without an answer, and returns to her own spreadsheet.	UXR-01
Quote	Marcus: "I don't need more dashboards, I need to know which one to trust."	UXR-02
Quote	Sam: "If I can't explain it, I can't present it."	UXR-10
Behavior	Nadia's Excel export no longer matched the dashboard a week later, and she couldn't tell which version was current.	UXR-11
Defect	Search matches only exact report names, so Priya's search fails.	BUG-2042
Defect	Attendance is defined three ways, and certified dashboards disagree.	BUG-2058
- **Your journey map, a shareable link, or the map file you committed (e.g. journey-map.html):** https://poe.com/invite/88567cf4082e4bbdb17c6ea94bfa4093
