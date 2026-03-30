# PRD: Episode Tracker & Release Calendar

**Author:** Pav Sabanathan  
**Created:** March 2026  
**Status:** V4 Released March 2026  
**Version:** 4.0

---

## 1. Problem Statement

Streaming services have fragmented how we watch TV. A viewer in 2026 
might have active subscriptions across Netflix, Disney+, Apple TV+, 
Prime Video, and traditional broadcast (e.g. BBC, Channel 4), with 
shows releasing on different days, at different cadences, with no 
single place to track it all.

The result is a common frustration: forgetting a new episode has 
dropped, losing track of where you are across multiple shows, or 
missing the start of a new season entirely.

There is no dedicated tool that combines a personal watchlist with 
automatic calendar integration for episode releases.

---

## 2. The User

**Primary User: The Multi-Platform Viewer**  
Someone who actively watches 3+ shows simultaneously across 2 or more 
streaming services. They are engaged enough to care about not missing 
episodes, but currently rely on memory, Reddit, or accidental 
discovery to know when something new drops.

**That user is currently me.** This product was born from my own 
frustration managing shows across multiple platforms with no reliable 
way to track release schedules in one place.

---

## 3. User Goals

- Know exactly when a new episode of any show I'm watching is released
- See all upcoming episodes across all platforms in one calendar view
- Never accidentally discover I'm three episodes behind on a show
- Easily add or remove shows as I start or finish them

---

## 4. Success Metrics

| Metric | Target |
|---|---|
| User can add a show and see release schedule | Under 60 seconds |
| Calendar correctly reflects real release dates | 95% accuracy |
| User returns to check the calendar weekly | Core retention signal |
| Shows from at least 5 major platforms supported | MVP requirement |

---

## 5. Core Features (MVP)

### 5.1 Show Search & Add
- User searches for a TV show by name
- Results show the show title, platform, and current status 
  (ongoing / ended / upcoming)
- User adds it to their personal tracker with one click

### 5.2 Episode Release Calendar
- A calendar view (week and month) showing upcoming episode 
  release dates for all tracked shows
- Each entry shows: show name, season number, episode number, 
  platform, and release date/time
- Colour coded by streaming platform for quick scanning

### 5.3 Streaming Platform Support (MVP)
- Netflix
- Disney+
- Apple TV+
- Prime Video
- BBC iPlayer
- A manual entry option for anything not covered

### 5.4 Show Management
- View all currently tracked shows in a simple list
- Mark a show as paused (still tracked but muted from calendar)
- Remove a show entirely when finished

### 5.5 Notifications (Post-MVP)
- Optional reminder the day before a new episode drops
- Weekly digest of everything releasing that week

---

## 6. What This Is NOT (Scope Boundaries)

- Not a streaming aggregator — we do not host or link to content
- Not a review or rating platform
- Not a social product at MVP — no sharing or friend features
- Not a recommendation engine at MVP

These are deliberate decisions to keep the MVP focused. Each could 
be a future phase.

---

## 7. Key Product Decisions & Reasoning

**Why calendar-first rather than notification-first?**  
Notifications require permissions and infrastructure. A calendar view 
delivers immediate value on first use with no setup friction. 
Notifications are a natural post-MVP layer once the core habit is 
established.

**Why include manual entry?**  
Data coverage for smaller or regional platforms will be imperfect at 
launch. Rather than showing an error state, a manual entry option 
keeps the product useful for 100% of a user's watchlist from day one.

**Why colour code by platform rather than genre?**  
The primary mental model for a multi-platform viewer is "what's on 
Netflix this week" vs "what's on Disney+." Platform is the organising 
principle that maps to real user behaviour.

---

## 8. Open Questions

- Which API will power the show and episode data? 
  (TVDB, TMDB, and TVmaze are leading candidates)
- How do we handle shows with inconsistent release schedules 
  (e.g. dropped all at once vs weekly)?
- How far in advance do streaming services publish episode dates, 
  and how do we handle gaps in that data?

---

## 9. What I'd Build Next (Post-MVP)

- Push notifications for episode releases
- Google Calendar / Apple Calendar sync
- "Catch me up" feature — shows episodes missed while paused
- Social layer — share your watchlist or see what friends are watching
- Mobile app version

---

## 10. Success Looks Like

A viewer sits down on a Sunday evening, opens the app, and in under 
10 seconds knows exactly what's dropping for them that week across 
every platform they use. They never miss an episode of something 
they care about again.
