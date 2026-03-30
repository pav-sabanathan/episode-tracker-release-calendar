# Case Study: Plotify — Episode Tracker & Release Calendar

> A PM with no engineering background, a real problem, and a PRD. Here's what happened next.

---

| | |
|---|---|
| **Author** | Pav Sabanathan |
| **Started** | March 2026 |
| **Status** | ✅ V4 Live |
| **Built With** | Lovable |
| **Live Product** | [Plotify](https://getplotify.vercel.app) |
| **GitHub** | [View Repository](https://github.com/pav-sabanathan/getplotify) |

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

**External Research Validation**

Early product research conducted before the 
first line of code was written validated the 
core problem and approach. Key findings that 
informed the roadmap:

- The primary gap in existing trackers (Trakt, 
  TV Time, Hobi) is that calendar sync is either 
  paywalled, notification-centric, or limited 
  to static ICS exports that become obsolete 
  when schedules change
- TVMaze and Watchmode identified as complementary 
  APIs for V5 — TVMaze for scheduling data, 
  Watchmode for Canadian streaming availability
- The Canada/US regional discrepancy is a 
  documented gap in all existing US-centric 
  trackers — an opportunity for Plotify to 
  differentiate in its home market
- Dynamic Webcal subscription (polling-based) 
  identified as the correct long-term architecture 
  over static ICS downloads

This research is documented in the project 
repository and informed several backlog 
additions including Webcal dynamic subscription, 
spoiler-free calendar toggle, specials handling, 
and regional streaming accuracy.

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
PRD. The initial build process happened in three focused rounds:

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

**Round 3 — Pre-V2 Polish & Build Recovery**

The Pre-V2 Polish update (empty states, onboarding, error 
handling, favicon, feedback mechanism, and legal pages) 
initially failed due to a build error introduced when 
Lovable added the favicon to index.html. The error:

"end-tag-without-matching-open-element"

...was caused by a malformed HTML tag that broke the 
Vite build entirely, making the preview unresponsive. 
The fix prompt resolved the underlying HTML issue but 
the preview still wasn't reflecting the changes.

**What I did:**
Rather than continuing to iterate on a potentially 
unstable build, I made the deliberate decision to 
revert the repository to the last known good state 
and start the Polish update fresh. This decision cost 
time but removed the risk of compounding errors on 
top of an already broken foundation.

The Polish update was then split into two focused 
prompts rather than one combined prompt — the approach 
that had worked cleanly in the original V1 build:

- Prompt 1: Empty states, onboarding flow, and 
  error handling
- Prompt 2: Favicon, feedback mechanism, and 
  legal pages

Both prompts executed cleanly on the second attempt.

**Post-Polish — Branding, Persistence & Mobile Optimisation**

With the core Polish update shipped, a second round 
of improvements focused on three areas: branding, 
data behaviour, and mobile experience.

**V2 — Core Feature Expansion**

V2 introduced three major feature areas that 
transformed Plotify from a simple calendar 
tracker into a more complete TV companion product.

**Mock Show Database & Search**
The manual-entry-only model from V1 was replaced 
with a searchable mock database of 20+ current 
shows with real metadata — platform, release 
schedule, season, episode count, and description. 
Real-time search filters from 2 characters, and 
selecting a show auto-populates the calendar 
with upcoming episodes immediately. Manual entry 
remains available for shows not in the database.

The database was curated specifically for a 
Canadian and UK audience, reflecting the actual 
streaming landscape in both markets — including 
shows on BBC iPlayer, Disney+, Apple TV, and 
Prime Video alongside Netflix. Shows only 
available on unsupported platforms (Sky, HBO Max, 
Paramount+) are intentionally excluded from search 
and flagged as manual-entry only.

**ICS Calendar Export**
Each tracked show in My Shows gained an Export 
to Calendar button that generates a standards-
compliant .ICS file containing all upcoming 
episodes for the current season as individual 
calendar events. Compatible with Google Calendar, 
Apple Calendar, and Outlook. Generated entirely 
client-side with no backend dependency.

**Episode Watch Tracking**
Show posters in My Shows became interactive — 
tapping opens a Show Detail panel with a full 
episode list, per-episode checkboxes, a progress 
bar, and a bulk Mark All Watched action. A key 
UX decision was making the calendar an entry 
point for watch tracking too — tapping an 
episode pill on the calendar opens the Show 
Detail panel scrolled directly to that episode, 
reducing the steps needed to log a watched 
episode from the release schedule view.

**UX Fixes Discovered During Testing**
Two additional improvements were identified 
during V2 testing:

- The manual Add Show form had no way to 
  dismiss it once opened — a clear × button 
  was added to collapse the form and return 
  to the default search state
- Form state was not preserved when navigating 
  between tabs — mid-entry data was lost if 
  the user switched to Home or My Shows. 
  Session-level state persistence was added 
  so all form fields are restored on return

Both fixes were implemented as a focused prompt 
between V2 Prompt 1 and Prompt 2 to avoid 
introducing conflicts into an already complex 
update.

**Branding**
A Plotify logo was designed in Canva and integrated 
into the app header. Key decisions along the way:
- Background removal was required to avoid the logo's 
  dark rectangle appearing on the app's dark background 
  at larger sizes
- The logo was made interactive — clicking it returns 
  the user to the Home screen from any tab, following 
  standard web navigation conventions
- A fallback poster was designed for manually added 
  shows using show initials (e.g. F.G. for Family Guy) 
  since no artwork API is available at this stage

**Data Persistence**
Before going public on LinkedIn, the default app 
state was corrected. The original build seeded sample 
shows on every first visit — meaning any new visitor 
who hadn't manually reset their localStorage would 
see pre-populated data rather than the intended 
onboarding experience.

The fix removed sample data seeding entirely, 
implemented proper localStorage persistence for 
user-added shows, and removed the developer Reset 
App Data button that had been used for testing. 
Every new visitor now sees the clean onboarding 
flow by default, and any shows they add persist 
across sessions and page refreshes.

**Mobile Optimisation**
Testing on a OnePlus 13 running Android Chrome 
revealed a persistent layout issue: the footer 
links (Privacy Policy, Terms of Service, Send 
Feedback) were not visible without scrolling 
due to Android Chrome's dynamic address bar 
behaviour affecting viewport height calculations.

After five iterations attempting CSS-based fixes 
(100dvh, fixed positioning, space-between flex, 
absolute positioning), the root cause was 
identified as a UX pattern mismatch rather than 
a technical problem — footer links are a desktop 
convention and do not belong on a mobile home 
screen. The correct solution was to move these 
links to the Settings page, which is where mobile 
users expect to find them.

This decision also prompted adding Settings as 
a permanent tab in the bottom navigation bar, 
improving discoverability of app preferences 
and legal links.

**Key learning:** Sometimes a persistent UI bug 
is a signal that the design pattern itself is 
wrong for the context, not just the implementation. 
Recognising when to change the approach rather 
than continue fixing the same problem is a 
valuable instinct in both engineering and product.
**The Reset Button Problem**

During testing of the onboarding flow and empty states, 
a secondary issue emerged. A "Reset app data" button 
had been added as a developer testing utility, but 
clicking it caused the sample shows to persist even 
after the reset. The root cause, identified through 
Lovable's own reasoning:

*"The page reloaded but shows are back — this is 
because loadShows() returns SAMPLE_SHOWS when there's 
no localStorage key (first visit). The reset clears 
localStorage, so the reload sees no key and re-seeds 
with samples. I need to set a flag during reset so 
the app knows it was intentionally cleared."*

In plain English: clearing the data and reloading 
the app triggered the same logic that runs on first 
visit — which re-seeds the app with sample shows 
automatically. The fix was to write a separate flag 
to localStorage during a reset, telling the app to 
treat the reload as an intentional clean state rather 
than a genuine first visit.

**Key process learning:** A combined prompt that 
tries to do too much in one generation increases 
the risk of subtle conflicts in the output. Smaller, 
focused prompts are more predictable and easier to 
debug when something goes wrong. This mirrors a 
principle from software development — small, 
atomic commits are easier to revert than large, 
sweeping changes.

**V3 — Landing Page & Analytics**

V3 introduced the public-facing layer of Plotify — 
a landing page that gives first-time visitors 
context before entering the app, and analytics 
infrastructure to start measuring real user 
behaviour.

**Landing Page**
The landing page sits at the root URL and serves 
as the product's public face. It covers the core 
value proposition, how the product works, and a 
features highlight with real app screenshots. 
Returning users who already have shows saved in 
localStorage bypass it automatically and land 
directly in the app — preserving the experience 
for existing users while giving new visitors the 
context they need.

The footer retains Privacy Policy and Terms of 
Service links — a deliberate decision to keep 
legal links on the public-facing page where 
visitors expect them, while Send Feedback remains 
inside the app under Settings only.

**PostHog Analytics**
V3 introduced the first real instrumentation of 
Plotify. PostHog was selected for its generous 
free tier, React SDK, and the combination of 
Product Analytics, Session Replay, and Error 
Tracking in a single platform.

Custom events were defined across both the 
landing page (landing_page_viewed, cta_clicked, 
how_it_works_viewed, features_viewed) and the 
core app (app_opened, show_added_search, 
show_added_manual, episode_marked_watched, 
ics_exported, onboarding_completed).

API keys are stored as Vercel environment 
variables and never hardcoded in source — 
a deliberate decision to treat this as a 
production-grade implementation rather than 
a throwaway portfolio project.

**Additional Improvements**
- Alphabetisation fixed across all show lists — 
  leading articles (The, A, An) excluded from 
  sort order, a known failure point in most 
  existing TV trackers
- Delete confirmation modal added to My Shows — 
  destructive actions should always require 
  confirmation to prevent accidental data loss 
  including watch progress

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
