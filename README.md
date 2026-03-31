# 📺 Plotify — Episode Tracker & Release Calendar

> Never miss an episode again. Track all your shows across every 
> streaming platform in one place.

---

| | |
|---|---|
| **Status** | ✅ V4 — Settings & Custom Platforms |
| **Built With** | Lovable · Vercel |
| **Live Product** | [getplotify.vercel.app](https://getplotify.vercel.app) |
| **Roadmap** | [View Roadmap](./ROADMAP.md) |
| **Case Study** | [View Case Study](./case-study/CASE_STUDY.md) |

---

## The Problem

Streaming is fragmented. Shows release across Netflix, Disney+, 
Apple TV, Prime Video, and BBC iPlayer — with no single place 
to track when new episodes drop. Plotify solves that.

---

## What's in This Repo

This repository contains the full product thinking behind Plotify — 
not the application code. Every decision, from problem identification 
through to build and iteration, is documented here.

| File / Folder | Contents |
|---|---|
| [PRD.md](./PRD.md) | Full product requirements document |
| [ROADMAP.md](./ROADMAP.md) | Version roadmap and upcoming features |
| [/case-study](./case-study/CASE_STUDY.md) | End-to-end case study write-up |
| [/research](./research/) | User research notes and findings |
| [/decisions](./decisions/) | Key product decisions and reasoning |

---

## The Build

Plotify was built using Lovable, an AI-native web app builder, 
using a detailed PRD-informed prompt. The full story of how it 
was built — including the prompts used, the decisions made, and 
what was changed between iterations — is documented in the 
case study above.

**Current Version:** V4 — Settings & Custom Platforms  
**Status:** Live at getplotify.vercel.app

**What's in V4:**

* Settings page accessible from all screens via cog icon
* Built-in streaming services displayed with platform colours
* 10 suggested platforms with one-tap add (Crave, Paramount+,
  Max, Crunchyroll, Sky, NOW TV, Channel 4, ITVX, Peacock, BritBox)
* Custom streaming service creation with hex colour input
* Custom platforms populate Add Show dropdown dynamically
* Platform accent colours applied consistently across show cards,
  badges, calendar pills, and Up Next strip
* Display preferences toggle — show/hide past 30 days of episodes
* Spoiler-free calendar export toggle
* Feedback mechanism surfaced in Settings
* About section with version and tagline

**Application code** lives in the companion repository: 
[github.com/pav-sabanathan/plotify](https://github.com/pav-sabanathan/plotify)
