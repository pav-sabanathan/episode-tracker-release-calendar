# Plotify — Product Roadmap

> This roadmap reflects the current development plan for Plotify. 
> It is a living document and will be updated after each version ships.

**Last Updated:** March 2026  
**Current Version:** V2 — Core Feature Expansion Live  
**Live Product:** [getplotify.vercel.app](https://getplotify.vercel.app)  

---

## ✅ V1 — MVP (Shipped March 2026)

The core product. Built in Lovable using a detailed PRD-informed 
prompt, deployed independently on Vercel.

- Dashboard with Up Next strip and week/month calendar toggle
- My Shows grid with platform colour coding and poster artwork
- Add Show with search and full manual entry form
- Platform support: Netflix, Disney+, Apple TV+, Prime Video, 
  BBC iPlayer
- Full season drop handling (single calendar entry)
- Mid-season add support (past episodes greyed out)
- Pause and remove show functionality
- Dark mode aesthetic with per-platform accent colours
- Fully responsive — desktop and mobile

---

## 🔧 Pre-V2 Polish — ✅ Complete

- [x] Empty states (Home, My Shows, Search)
- [x] First-time onboarding flow (3-step modal)
- [x] Form validation and error handling
- [x] Duplicate show detection with toast
- [x] Success/error toast notifications
- [x] Favicon (PNG, icon mark only, transparent background)
- [x] In-app feedback mechanism (mock)
- [x] Privacy Policy page
- [x] Terms of Service page
- [x] Footer with Privacy/Terms links (desktop)
- [x] Remove sample data — clean empty state as default
- [x] localStorage persistence for user-added shows
- [x] Remove Reset App Data developer utility
- [x] Release day bug fix — episodes mapping to correct weekday
- [x] Number input bug fix — Season and Episode fields
- [x] Logo added to header (transparent PNG)
- [x] Show initials fallback poster (e.g. F.G. for Family Guy)
- [x] Logo clickable — returns user to Home from any screen
- [x] Mobile layout optimised for Android Chrome
- [x] Footer links moved to Settings on mobile
- [x] Settings added to bottom navigation bar

---

## 🚀 V2 — Core Feature Expansion — ✅ Complete

- [x] Mock IMDb-style show database with real-time search
- [x] Auto-population of calendar on show add via search
- [x] ICS calendar export per series (Google, Apple, Outlook)
- [x] Episode watch tracking with per-episode checkboxes
- [x] Watch progress indicator on My Shows cards
- [x] Show detail panel with full episode list
- [x] Calendar episode pills link directly to Show Detail 
      panel for direct watch tracking access
- [x] Dismiss button on manual Add Show form
- [x] Add Show form state persists across tab navigation
- [x] Export to Calendar button colour standardised 
      to white across all platforms
- [x] ICS file Android compatibility fixed — 
      CRLF line endings, required VEVENT fields, 
      UTC timestamp
- [x] Favicon updated to icon mark only (no wordmark)
- [x] Total Episodes field added to manual Add Show form
- [x] First Episode Date field added to manual Add Show form
- [x] Season Complete status on final episode air date
- [x] Edit functionality for manually added shows
- [x] Release Time and First Episode Date icons changed to white
- [x] iPad modal overflow fixed — Release Day/Time fields
- [x] Vercel client-side routing fix — 404 on direct URL access resolved

---

## 📋 V3 — Landing Page — In Planning

A public-facing landing page that gives first-time visitors 
context before entering the app.

- Hero section with headline, subheadline, and CTA
- Platform social proof bar
- How It Works — three-column feature explainer
- Features highlight with app screenshots
- Footer with Privacy Policy and Terms of Service placeholders
- "Try Plotify Free" CTA throughout

---

## ⚙️ V4 — Settings & Customisation — In Planning

Giving users control over their experience and expanding 
platform coverage beyond the built-in list.

- Settings menu accessible from all screens
- Custom streaming service creation with colour picker
- Custom services populate Add Show dropdown dynamically
- Display preferences toggle (show/hide past episodes)
- About section with version history
- Feedback mechanism surfaced in settings

---

## 🔐 V5 — Authentication & Data Persistence — In Planning

The milestone that takes Plotify from demo to real product. 
Requires Supabase integration — architectural review with 
engineering collaborator before starting.

- Supabase authentication (email/password + Google OAuth)
- User account creation and sign-in flow
- Cross-device data persistence for all show and 
  watch progress data
- Guest mode with sign-in prompt for unauthenticated users
- User avatar and account menu in app header
  
### 🔭 V5 — Additional Scope Note
Replace mock show database (introduced in V2) with 
a live TMDb API integration. API key to be stored 
server-side via Supabase to avoid front-end exposure. 
Attribution required: "This product uses the TMDb 
API but is not endorsed or certified by TMDb."

**New season detection:** On app open, Plotify checks 
TMDb for premiere date updates on shows marked as 
"ended" or "between seasons" in the user's watchlist. 
If a new season premiere date is found, the calendar 
is updated automatically and the user is notified 
via toast. Scope: V5 alongside TMDb integration.

## 🏆 V6 — Badges & Achievement System — Planned

A retention and reward mechanic that gives users 
a sense of achievement for watching and tracking 
shows across Plotify.

### Core Concept
Genre-based badge collection with tiered milestones, 
inspired by achievement systems in apps like OnePlus 
Red Cable Club and Pokémon TCGP. Users collect badges 
by watching episodes across different show categories, 
with bronze/silver/gold/platinum tiers per genre.

### Badge Categories
Genre badges powered by TMDb genre classification 
(introduced in V5). Each watched episode counts 
toward all applicable genres simultaneously:

- 🎭 Drama
- 😂 Comedy  
- 🎬 Action & Adventure
- 🚀 Sci-Fi & Fantasy
- 🔍 Crime
- 🎨 Animation
- 🍣 Anime (Animation + Japanese origin)
- 📺 Reality
- 📰 Documentary

### Tier Thresholds (per genre)
| Tier | Episodes Watched |
|---|---|
| Bronze | 25 |
| Silver | 100 |
| Gold | 500 |
| Platinum | 1000 |

### Special Badges
Time-limited and milestone badges outside of 
genre categories:
- 🎂 Plotify Anniversary — issued annually 
  on the user's signup anniversary date
- 🔥 Binge Badge — 5+ episodes of the same 
  show watched within 24 hours
- 📅 Streak Badge — episodes logged on 
  consecutive days (7, 30, 100 day tiers)
- 🏁 Season Complete — finish an entire season
  (already implemented in V2 as a status — 
  could be formalised as a badge)

### Trophy Design
A combination of the five major TV awards 
aesthetics (BAFTA, Emmy, Golden Globe, SAG, 
Critics Choice) rendered as tiered trophies:
- Bronze — copper/brown finish
- Silver — silver/chrome finish  
- Gold — gold finish
- Platinum — iridescent/holographic finish

### Technical Dependencies
- ✅ Watch progress tracking (V2)
- ⬜ User authentication (V5)
- ⬜ Supabase database for badge progress (V5)
- ⬜ TMDb genre classification (V5)

### UI Placement
Dedicated Badges tab or section within a 
future Profile screen. Includes:
- Badge collection grid (locked/unlocked states)
- Progress bar per badge showing episodes 
  toward next tier
- Profile summary showing total episodes 
  tracked and badges earned
- Achievement Showcase — 3 pinned badges 
  chosen by the user
- Time-limited badge section

### Key Design Decisions
- Watched episodes count toward ALL applicable 
  genre badges simultaneously — rewards users 
  fairly given how multi-genre most prestige 
  TV is
- Badge progress stored server-side in Supabase 
  tied to user account — enables cross-device 
  sync and future social/sharing features
- Anniversary badges issued on signup 
  anniversary date — drives annual retention

### Why V6 and not earlier
Badge progress needs to be tied to authenticated 
user accounts to persist across devices and 
support the social/discussion angle. Building 
on localStorage would severely limit the feature. 
V5 authentication and Supabase are hard 
dependencies.

## 📋 Additional Backlog — Research Identified

Features and considerations identified during early 
product research that complement the existing roadmap.

### Product Features

- **Webcal dynamic subscription** — upgrade from 
  static ICS download to a polling-based subscription 
  URL (webcal://). Users subscribe once and their 
  calendar updates automatically when schedules 
  change. Requires server-side endpoint — V5 
  dependency. Addresses the core limitation of 
  static ICS files becoming obsolete when networks 
  change scheduling (e.g. double episodes, 
  schedule shifts)

- **Spoiler-free calendar toggle** — Settings option 
  to exclude episode descriptions from ICS/Webcal 
  exports. Prevents calendar notifications from 
  spoiling unwatched episodes. Scope: V4 Settings

- **Specials and bridge episodes** — chronological 
  integration of specials into the main season 
  timeline rather than a separate category. 
  Addresses the "Doctor Who problem" common in 
  existing trackers where Christmas specials and 
  bridge episodes are incorrectly sequestered 
  outside the seasonal calendar. Scope: V5/TMDb

- **Canada/US regional streaming discrepancy** — 
  differentiate between US broadcast dates and 
  Canadian streaming availability dates. A show 
  airing Sunday on Fox in the US may not be 
  available on Disney+ Canada until a different 
  day. Watchmode API supports country=CA parameter 
  for regional accuracy. Scope: V5

- **Alphabetisation fix** — sort show titles 
  ignoring leading articles (The, A, An) so 
  "The Bear" sorts under B not T. Common failure 
  point in existing trackers. Scope: V3/V4 polish

### API Evaluation Notes

- **TVMaze** — evaluate alongside TMDb for V5 
  integration. Key advantages: dedicated 
  /schedule and /schedule/full endpoints designed 
  for calendar use cases, free with no commercial 
  restrictions (CC BY-SA attribution), supports 
  IMDb IDs as lookup keys. TMDb remains stronger 
  for poster images and genre classification. 
  A hybrid approach (TVMaze for scheduling, 
  TMDb for metadata/images) may be optimal

- **Watchmode** — evaluate for V5 Canadian 
  streaming availability. Provides country-specific 
  streaming data (country=CA) to resolve 
  Canada/US discrepancies. 1,000 free requests 
  per month on free tier

### Portfolio and IP Notes

- Thorough documentation of prompt engineering 
  and architectural decisions (decisions log, 
  case study) serves dual purpose — strengthens 
  portfolio signal AND demonstrates "sufficient 
  human skill and judgment" required for Canadian 
  copyright protection of AI-assisted work

- Open source licence on GitHub (MIT) provides 
  portfolio visibility while clearly defining 
  terms of reuse. No patent filing recommended 
  for a portfolio project at this stage

### Additional Tools and Infrastructure

- **PostHog** — add to V3 scope. Instrument 
  analytics on the landing page and core app 
  events (show added, episode marked watched, 
  ICS exported). Free tier sufficient for 
  current scale. Provides real usage data to 
  inform future prioritisation decisions

- **Namecheap custom domain** — getplotify.com 
  or getplotify.app. ~$15-30/year. Independent 
  of build work, can be done any time

- **SimpleLogin** — email forwarding from 
  custom domain (e.g. hello@getplotify.com). 
  Add to V5 scope alongside authentication

- **Formspree** — optional waitlist or contact 
  form on V3 landing page. Low effort addition 
  if needed

- **TestFlight / Xcode** — Apple beta 
  distribution and native iOS build tooling. 
  V7 scope alongside React Native rebuild

- **RevenueCat** — in-app purchase and 
  subscription management for App Store and 
  Play Store. V8 scope

- **Rotato / CapCut** — 3D device renders 
  and App Store trailer editing. V8 scope

- **SQLite** — local database caching layer 
  for React Native. Evaluate for V7 alongside 
  Supabase real-time sync
  
---

## 🔭 Future Versions — Backlog

Features under consideration for post-V5 development, 
subject to user feedback and validation.

### Web Backlog (V6+)

- Badges & Achievement System — genre-based trophy 
  collection with tiered milestones (Bronze/Silver/
  Gold/Platinum). Full scope documented in V6.
- "Catch Me Up" feature for shows you've fallen 
  behind on — summarises how many episodes behind 
  you are and what you missed
- Recommendation engine based on watch history — 
  suggest new shows based on genres and platforms 
  already tracked
- Social layer — share watchlist, see what friends 
  are watching, compare badge collections
- Google Calendar and Apple Calendar native sync — 
  automatic two-way sync beyond current ICS export. 
  Note: ICS export (V2) covers most use cases in 
  the interim
- New season detection — automatic calendar update 
  when a new season premiere date is announced for 
  a tracked show (scoped for V5 alongside TMDb 
  integration)

### App Store / Play Store — Future Roadmap

A native mobile app launch is a post-V5 goal 
and represents a significant separate workstream. 
The following are required for store submission:

**Must-haves:**
- Mobile app rebuild in React Native / Expo — 
  the current web app is not submittable to 
  either store. React Native is the natural 
  choice given the existing React codebase — 
  logic, data structures, and Supabase 
  integration carry over directly
- Push notifications — episode dropping 
  tomorrow alerts. Core user expectation 
  for a native tracker app. Achievable via 
  React Native notification libraries once 
  the mobile rebuild is underway
- Social layer — without social features 
  Plotify competes directly with established 
  apps (TV Time, Serializd, Letterboxd) that 
  already have large communities. A 
  differentiated social angle is important 
  for store discoverability and retention

**Nice to have at launch:**
- Badges & Achievement System (V6) — strong 
  retention mechanic and social discussion 
  driver, particularly valuable at app launch
- Recommendation engine — valuable for 
  engagement but complex to build well. 
  Could ship post-launch based on feedback
- Catch Me Up — useful but niche, not a 
  blocker for store submission

**Dependency chain for store launch:**
```
V3 — Landing page
V4 — Settings & custom services  
V5 — Authentication & Supabase + TMDb integration
V6 — Badges & achievement system
V7 — React Native rebuild
V8 — Push notifications + App Store/Play Store submission
```

### Note on React Native Migration
The existing React component structure and 
Supabase integration make the V7 migration 
more straightforward than a ground-up rebuild. 
Core business logic, API calls, and data 
models carry over directly. The primary 
workload is rebuilding the UI layer in 
React Native and integrating platform-specific 
features (push notifications, native date 
pickers, app store assets).

---

## 📊 Roadmap Principles

Every version of Plotify is guided by three questions:

1. **Does this solve a real problem for a real user?**
2. **Is this the smallest version that delivers genuine value?**
3. **Does this create the foundation for what comes next?**

Features that can't answer yes to all three get pushed 
to a later version or removed entirely.

---

## 📎 Related Documents

| Document | Description |
|---|---|
| [PRD.md](./PRD.md) | Full product requirements document |
| [case-study/CASE_STUDY.md](./case-study/CASE_STUDY.md) | End-to-end case study |
| [decisions/](./decisions/) | Individual product decision logs |
