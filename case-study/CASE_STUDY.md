# Case Study: StreamLine — Episode Tracker & Release Calendar

**Author:** Pav Sabanathan
**Started:** March 2026
**Status:** MVP Live
**Built With:** Lovable
**Live Product:** [StreamLine](https://watch-track-sync.lovable.app)

---

## 1. The Problem

Streaming is fragmented. In 2026 a typical viewer might have active 
subscriptions across Netflix, Disney+, Apple TV+, Prime Video, and 
BBC iPlayer — with shows releasing on different days, at different 
cadences, across different platforms.

The result is a frustratingly common experience: forgetting a new 
episode has dropped, losing track of where you are across multiple 
shows, or missing the start of a new season entirely.

This wasn't a hypothetical problem. It was my problem. I was 
personally managing five active shows across four platforms with 
nothing but memory and occasional Reddit threads to tell me when 
something new dropped. That frustration became this product.

---

## 2. The User

**Primary user: Me.**

Rather than inventing a persona, I used myself as the primary user 
for MVP. I am an active multi-platform viewer tracking 5+ shows 
simultaneously, with subscriptions across Netflix, Disney+, Apple 
TV+, Prime Video, and BBC iPlayer.

Using myself as the user had a deliberate advantage at MVP stage — 
I had instant, honest access to feedback and could validate 
assumptions in real time without needing to recruit research 
participants.

**Who this scales to:**
Any viewer actively watching 3+ shows across 2 or more streaming 
platforms who wants to stop relying on memory or accidental 
discovery for release dates.

---

## 3. Discovery & Research

Before writing a single line of product specification I documented 
the problem in a PRD (see PRD.md). Key questions I worked through:

- What is the actual moment of frustration? (Discovering you're 
  behind, not missing a release in real time)
- What does the user mental model look like? (Platform-first, 
  not genre-first — "what's on Netflix this week")
- What already exists? (Trakt.tv, TV Time — both overcomplicated 
  for casual viewers, too social, not calendar-native)
- What is the minimum that delivers real value on day one?

The insight that shaped the MVP most: **calendar-first beats 
notification-first.** Notifications require permissions and 
infrastructure. A calendar view delivers immediate value on first 
visit with zero setup friction.

---

## 4. Key Product Decisions

### Decision 1: Dashboard landing screen over calendar-only
I chose a combined dashboard (Up Next strip + Calendar) as the 
landing screen rather than dropping users directly into a calendar. 

**Why:** The Up Next strip answers the most common immediate 
question — "what's on soon?" — without requiring the user to 
navigate or interpret a calendar. The calendar below it provides 
the fuller picture for users who want it. Two user needs, one 
screen, clear hierarchy.

### Decision 2: Colour coding by platform, not genre
Every episode pill on the calendar is coloured by streaming 
platform rather than genre.

**Why:** The primary mental model for a multi-platform viewer 
is "what's on Netflix this week" vs "what's on Disney+." Platform 
is the organising principle that maps to real behaviour. Genre 
would have been intellectually interesting but practically less 
useful.

### Decision 3: Full season drops as a single calendar entry
For shows that release an entire season at once (e.g. Netflix 
originals), I chose to display a single calendar entry labelled 
"[Show] S[X] — All Episodes" rather than one entry per episode.

**Why:** Multiple entries for the same release date creates 
visual noise with no added value. The user's action is the same 
regardless — open the platform and watch. One clean entry 
communicates everything they need.

### Decision 4: Manual entry as a first-class feature
Rather than leaving a gap for platforms or shows not covered 
by search, I built manual entry as a deliberate, clearly 
signposted option from day one.

**Why:** Data coverage for smaller or regional platforms will 
always be imperfect. An error state or missing shows would 
break trust in the product immediately. Manual entry keeps 
the app useful for 100% of a user's watchlist from day one, 
at the cost of some user effort — a trade-off worth making at MVP.

### Decision 5: No login at MVP
The app runs entirely on local state with no authentication.

**Why:** Login adds friction, infrastructure complexity, and 
a reason to drop off before experiencing the product's core 
value. For a single-user MVP the trade-off is obvious — 
remove the barrier, validate the core experience first.

---

## 5. How It Was Built

StreamLine was built using Lovable, an AI-native web app builder, 
using a detailed natural language prompt informed directly by the 
PRD. The build process happened in two focused rounds:

**Round 1 — Initial build prompt**
A comprehensive specification covering: dashboard layout, Up Next 
strip, calendar with week/month toggle, My Shows grid, Add Show 
with search and manual entry, platform colour system, dark mode 
aesthetic, and pre-populated sample data.

**Result:** A working, visually polished MVP with all core screens 
present and the platform colour system correctly applied.

**Round 2 — Refinement prompt**
Five targeted fixes identified through review of the first build:
1. Calendar view state not persisting between tab navigation
2. No scroll arrows on the Up Next strip
3. Add Show button visually greyed out
4. Fallout incorrectly labelled "Ongoing" instead of 
   "All Episodes Available"
5. Slow Horses missing its platform border

**Result:** All five fixes applied cleanly in a single prompt.

**Key process learning:** Writing the PRD before opening the 
builder made the first prompt significantly more precise. The 
product decisions were already made — the prompt was simply 
translating them into instructions. This discipline is worth 
carrying into every AI-assisted build.

---

## 6. What I'd Build Next

**Phase 2 — Notifications**
Push notifications the day before a new episode drops, and a 
weekly digest of everything releasing that week. This is the 
natural next layer once the calendar habit is established.

**Phase 3 — Calendar Sync**
Export to Google Calendar or Apple Calendar so episode releases 
live alongside the rest of a user's life, not in a separate app.

**Phase 4 — Catch Me Up**
A feature for shows where you've fallen behind — surface the 
episodes you've missed and how long it would take to catch up 
before the next release.

**Phase 5 — Social Layer**
Share your watchlist, see what people you follow are watching, 
get recommendations based on mutual shows. This is the point 
where the product becomes a network rather than a personal tool.

---

## 7. What I Learned

**On product process:** Starting with a PRD — even a lightweight 
one — before touching any tooling forces clarity that pays off 
immediately. The decisions made on paper meant fewer wasted 
iterations in the builder.

**On AI-assisted building:** Specificity in prompting is 
everything. Vague prompts produce vague results. The more 
precisely you can describe the behaviour, layout, and logic 
you want, the closer the first output will be to your vision.

**On scope:** The deliberate decision to exclude notifications, 
social features, and calendar sync from MVP was the right call. 
A focused product that does one thing well is more impressive — 
and more useful — than a bloated one that does five things 
adequately.

**On using yourself as the user:** Valid at MVP stage, but the 
next step before any serious development investment would be 
5-10 user interviews with other multi-platform viewers to 
validate whether my frustrations are universal or personal.

---

## 8. Success Metrics (Revisited)

From the original PRD, the MVP targets were:

| Metric | Target | Result |
|---|---|---|
| Add a show and see release schedule | Under 60 seconds | ✅ Achieved |
| Calendar reflects real release dates | 95% accuracy | ✅ Sample data accurate |
| Shows from 5+ major platforms supported | MVP requirement | ✅ All 5 covered |
| Full season drops handled distinctly | Design requirement | ✅ Amber badge applied |
