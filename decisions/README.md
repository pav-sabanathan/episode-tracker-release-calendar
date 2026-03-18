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
| Logo as home navigation | Pre-V2 | Standard web convention — clicking a logo returns the user to the homepage, reducing navigation friction |
| Remove sample data seeding — empty state as default | Pre-V2 Polish | New visitors should experience the intended onboarding flow, not pre-populated data that gives a false impression of the product |
| Move footer legal links to Settings on mobile | Pre-V2 Polish | Footer links are a desktop convention — on mobile they belong in Settings where users expect to find them, and removing them fixed a persistent Android Chrome layout bug |
| Add Settings as permanent bottom nav tab | Pre-V2 Polish | Discoverability — with legal links and feedback moved to Settings, users need a clear way to find it without burying it behind a cog icon |
| Logo made interactive — click navigates to Home | Pre-V2 Polish | Standard web convention that reduces navigation friction from any screen |
| Show initials as fallback poster | Pre-V2 Polish | No artwork API available at this stage — initials (e.g. F.G.) are more informative than a generic TV icon and scale to any show name |
| Calendar pills link to watch tracking | V2 | Calendar should be an entry point for marking episodes watched, not just a passive release schedule view — reduces the steps needed to log a watched episode |
| Curate mock database for Canadian and UK streaming landscape | V2 | Target audience spans both markets — excluding unsupported platforms avoids user confusion |
| Manual entry remains alongside search | V2 | Search covers 20+ shows but cannot cover every show — manual entry ensures 100% watchlist coverage |
| Calendar pills as watch tracking entry point | V2 | Reduces steps to log a watched episode — calendar is already the primary navigation surface |
| ICS export generated client-side only | V2 | No backend dependency at this stage — client-side blob generation is sufficient and keeps architecture simple |
| Form state persists for session only, not across refreshes | V2 | Full persistence would require localStorage schema changes — session-only is sufficient for the UX problem being solved |
| Dismiss button added to manual Add Show form | V2 | No escape hatch once form was opened — × button restores expected interaction pattern |
| Export button standardised to white | V2 | Platform accent colours vary in brightness — white ensures consistent visibility in dark mode across all platforms |
| ICS Android fix — CRLF and required fields | V2 | Android calendar parsers are strict about line endings and mandatory VEVENT fields — LF-only files fail silently |
| Favicon changed to icon mark only | V2 | Wordmark unreadable at favicon scale — icon mark only improves brand recognition in browser tabs and bookmarks |
| First Episode Date field added to manual form | V2 | Release day alone had no start anchor — users needed a specific date to generate an accurate calendar regardless of when they add the show |
| Total Episodes field added to manual form | V2 | Without episode count the calendar had no stop condition and would generate episodes indefinitely |
| Season Complete status on final episode air date | V2 | Automatic status update removes manual housekeeping without removing the show from the watchlist |
| Edit functionality for manually added shows only | V2 | Database shows have fixed metadata — edit is only meaningful for user-defined manual entries |
| Vercel routing fix via vercel.json | V2 | React SPA routing requires all paths to serve index.html — without vercel.json direct URL access and page refresh returned 404 on all non-root routes |
| Badges count toward all applicable genres simultaneously | V6 | Most prestige TV is multi-genre — single primary genre classification would feel arbitrary and reward users less fairly |
| Badge system deferred to V6 post-authentication | V6 | localStorage-only badge progress would not persist across devices or support social features — Supabase user accounts are a hard dependency |
| Webcal dynamic subscription scoped to V5 | Backlog | Static ICS files become obsolete when schedules change — a polling-based subscription URL ensures calendar entries update automatically without user intervention |
| Spoiler-free calendar toggle scoped to V4 Settings | Backlog | Calendar notifications containing episode descriptions can spoil unwatched content — opt-in toggle gives users control over what appears in their calendar events |
| Specials and bridge episodes scoped to V5/TMDb | Backlog | Existing trackers incorrectly sequester specials outside the seasonal calendar — chronological integration is a known differentiator from competitors like Trakt |
| Canada/US regional streaming discrepancy scoped to V5 | Backlog | US broadcast dates and Canadian streaming availability dates differ — a show airing Sunday on Fox in the US may not be available on Disney+ Canada until a different day. Watchmode country=CA parameter identified as the solution |
| TVMaze evaluated as complement to TMDb for V5 | Backlog | TVMaze offers dedicated schedule endpoints ideal for calendar use cases and is free with no commercial restrictions — hybrid approach (TVMaze for scheduling, TMDb for metadata and images) may be optimal |
| Watchmode evaluated for Canadian streaming availability | Backlog | Provides country-specific streaming data to resolve Canada/US discrepancies — 1,000 free requests per month on free tier |
| Alphabetisation fix identified as V3/V4 polish item | Backlog | Common failure point in existing trackers identified during early research — sort titles ignoring leading articles so "The Bear" sorts under B not T |

---

## Adding New Decisions

As Plotify develops, each significant product decision will be 
added to this folder as its own markdown file, named clearly 
by topic — for example `calendar-vs-notifications.md` or 
`auth-approach-v5.md`.
