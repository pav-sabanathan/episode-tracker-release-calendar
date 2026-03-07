# Product Decisions

This folder documents the key product decisions made throughout 
the development of Plotify — including what was decided, why, 
and what alternatives were considered.

---

## Why This Folder Exists

Good product decisions deserve to be documented. This folder 
exists to create a transparent record of the thinking behind 
Plotify — not just what was built, but why it was built that way.

Each decision document follows the same structure:
- **The question** — what needed to be decided
- **The options considered** — what the realistic alternatives were
- **The decision** — what was chosen
- **The reasoning** — why this option over the others
- **The outcome** — how it played out in practice

---

## Decisions Log

| Decision | Version | Summary |
|---|---|---|
| Calendar-first over notification-first | V1 | Delivers immediate value on first visit with no setup friction |
| Platform colour coding over genre | V1 | Maps to real user mental model — "what's on Netflix this week" |
| Full season drops as single entry | V1 | Reduces visual noise with no loss of useful information |
| Manual entry as first-class feature | V1 | Keeps the app useful for 100% of watchlists from day one |
| No login at MVP | V1 | Removes friction to validate core experience first |
| PRD before prompt | V1 | Forced clarity that made the first Lovable build significantly more precise |
| Split Pre-V2 Polish into two prompts after build failure | Pre-V2 | Smaller focused prompts reduce conflict risk and are easier to debug and revert |
| Reset flag approach for developer testing utility | Pre-V2 | Clearing localStorage re-triggers first-visit seeding — a separate flag was needed to distinguish intentional resets from genuine first visits |
| Release day not mapping correctly to calendar | Pre-V2 | Manual add form was defaulting all shows to Friday regardless of selected day — fixed by correctly mapping weekday selection to calendar date calculation |
| Season and Episode number input appending instead of replacing | Pre-V2 | Number fields defaulted to 0 on clear and appended new input rather than replacing — fixed with proper empty state handling and input validation |

---

## Adding New Decisions

As Plotify develops, each significant product decision will be 
added to this folder as its own markdown file, named clearly 
by topic — for example `calendar-vs-notifications.md` or 
`auth-approach-v5.md`.
