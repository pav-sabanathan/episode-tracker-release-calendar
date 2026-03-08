# Plotify — Product Roadmap

> This roadmap reflects the current development plan for Plotify. 
> It is a living document and will be updated after each version ships.

**Last Updated:** March 2026  
**Current Version:** V1 — MVP Live  
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

## 🚧 V2 — Core Feature Expansion — In Planning

Expanding the core functionality based on the most valuable 
user needs identified post-MVP.

- Mock IMDb-style show database with real-time search
  (20+ shows pre-loaded with full metadata)
- Auto-population of calendar on show add via search
- ICS calendar export per series (Google, Apple, Outlook)
- Episode watch tracking with per-episode checkboxes
- Watch progress indicator on My Shows cards
- Show detail panel with full episode list

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

---

## 🔭 Future Versions — Backlog

Features under consideration for post-V5 development, 
subject to user feedback and validation.

- Push notifications (episode dropping tomorrow alerts)
- Google Calendar and Apple Calendar native sync
- "Catch Me Up" feature for shows you've fallen behind on
- Social layer — share watchlist, see what friends watch
- Mobile app (React Native / Expo)
- Recommendation engine based on watch history

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
